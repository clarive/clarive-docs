---
title: Running Shell Commands
index: 900
---

One of rulebooks main goals is to make it extremely easy to call out to shell commands.

Shell commands may be executed either locally (in the Clarive server) or
remotely (ie. in a remote node). You will need to decide where to execute your
commands.

## Running Commands Locally

Local commands run in a shell in the Clarive server, always inside a Docker
container.

```yaml
do:
     # This is the long way of executing a shell command:

    - shell:
        cmd: ls
        args:
           - "-l"
           - "-a"
```

Which, luckly, can be shortened to something along these lines:

```yaml
do:
    - shell: ls -la # oh, this is much better
```

If you'd prefer to separate your args, there's also a concise version:

```yaml
do:
     - shell:
         - apt
         - install
         - build-essential
         - openssl

     # which becomes "apt install build-essential openssl" in the shell
```

Or in concise array notation:

```yaml
do:
     - shell: [ 'apt', 'install', 'build-essential', 'openssl' ]

     # same, it becomes "apt install build-essential openssl" in the shell
```

Or better yet, using the direct notation. Unfortunately the direct notation
does not have an array argument (`args`), but is definitely the way to go.

```yaml
do:
    - ls -lart    # yes, this is much better
    - "ls -lart"  # ditto
```

If you need to run multiple commands at once you can separate them with newline:

```yaml
do:
    - shell:
        cmd: |
         echo hello >> /clarive/myfile
         echo world >> /clarive/myfile
         cat /clarive/myfile

    # or like this:

    - shell: |
         echo hello >> /clarive/myfile
         echo world >> /clarive/myfile
         cat /clarive/myfile

    # or yet:

    - |
         echo hello >> /clarive/myfile
         echo world >> /clarive/myfile
         cat /clarive/myfile
```


## Assigning the output to a variable

Now the best feature of rulebook shell commands is that you can assign command
values to variables. You need to prepend the `shell:` command with the variable
you want to use.

```yaml
do:
   - result = shell: ls -lart /clarive
   - echo: "exit code was ${result.rc}, output: ${result.output}"
```

Commands always return a hash object with 2 subkeys:

```yaml
{
   rc: 0,          # the exit code of the command
   output: '...'   # the capture output combining stderr and stdout
}
```

You can assign a multiline command sequence just the same, but you gotta use `shell:`:

```yaml
do:

    - ret = shell: |
         echo hello >> /clarive/myfile
         echo world >> /clarive/myfile
         cat /clarive/myfile

    - echo: "OUTPUT = {{ ret.output }}"
    - echo: "EXIT CODE OF LAST COMMAND = {{ ret.rc }}"
```

!!! note
    Failed shell commands (exit code <> 0) that are not assigned to variables will
    __throw errors__ that will interrupt your rulebook.

    Therefore, assigning commands to variables is a good way
    to __trap errors__ and process them yourself.

Here's an example of captured variable with error control:

```yaml
do:

    # capturing and error control combined

    - ret = shell: |
         ls -lart /clarive/
         ls -lart /clarive/this_folder_not_here

    - echo: "OUTPUT = {{ ret.output }}"

    - if: "{{ ret.rc }}"
      then:

         # use log: for colored output in the job log viewer

         - log:
              msg: "We failed with rc={{ ret.rc }}"
              level: error
      else:
         - echo: "Everything okay"
```

That will produce the following output:

    ls: cannot access '/clarive/not_exists': No such file or directory

    We failed with rc=2

#### Piping commands

Sometimes you may want to pipe several shell commands together, redirecting
output from one command to the next. This is quite trivial and it's managed
by the shell runner (a C `open3()` function):

```yaml
do:
    - cat /etc/hosts | wc -l
```

If you want to pipe the output back into your rulebook, then you should setup
a `stdout` or `stderr` callback. The shell process will invoke the
callback with chunks of output.

```yaml
do:
    - shell:
        cmd: find /
        pipe_out:
           - echo: "Got a stdout chunk here: ${chunk}"
```

Or process it with [ClaJS](/devel/intro) directly:

```yaml
do:
    - shell:
        cmd: find /
        pipe_out: |
           print( "Got it here now: " + cla.stash('chunk') );
```

## Selecting a Docker Image

Commands that run in the server __always run in a Docker container__.
By default, commands run on the [clarive default image](https://hub.docker.com/r/clarive/rulebook-runner/).
But you can easily control what container image is being used with the `image:` op.

```yaml
do:
    # download and install a python image from Docker Hub
    # (if you don't already have it installed)

   - image: python
   - python --version
```

You can alternate between images as you go:

```yaml
do:
    # python first

   - image: python
   - python --version

    # then ruby

   - image: ruby
   - ruby --version
   - gem install json
```

Or run it within an `image:` block with `do:`, which
groups it nicely:

```yaml
do:
    # watch out for correctly indenting image and do

   - image: ruby
   - do:
      - gem install json
      - gem install mongo
```

!!! important
    Each command that runs in a Docker image will
    `docker run -it` everytime. Use the multi-line commands
    shown above to run them in the same container run session.
