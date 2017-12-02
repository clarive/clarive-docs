---
title: The Rule Cookbook
index: 9000
---

This document is a (somewhat) random batch of recipes in case you
just prefer a learn-by-example approach.

Happy cooking!

#### Hello World!

```yaml
do:
  - echo: "Hello World!"
```

#### Running the Hello World above

The easiest way is to use the web REPL in
your Clarive installation.

Just point your browser here:

    https://yourclariveserver/r/repl

Write some code and hit Ctrl-Enter (Windows/Linux)
or Cmd-Enter (Mac) to run it.

#### Putting comments in your code

```yaml
do:
   # now for some hello-worldly stuff
   - print: Hello
   - print: World!    # here me comment ok is too
```

#### Declaring programwise variables

```yaml
vars:
   myvar: World
do:
   - echo: Hello ${myvar}
```

#### Iterating over an array

```yaml
vars:
   - myarray:
       - 1
       - 2
       - 3
do:
   - foreach:
       var: mycounter
       in: ${myarray}
       do:
          - echo: Hello number ${mycounter}
```

#### Creating and changing a Topic

```yaml
do:
   - mid = create_topic:
          category: Enhancement
          data:
            description: |
                 Just a short description
          status: New
          title: My topic title

   - update_topic:
         mid: ${mid}
         data:
            title: 'Changed it just now'

   - change_status:
        mid: ${mid}
        to: Fixed
```

#### Calling a web-service

```yaml
do:
   - request:
      url: http://jsonplaceholder.typicode.com/posts
      method: POST
      returning: res
   - print: hello ${res.content}
```

#### Show the server you are deploying to in the job log

Use variables in decorators to customize your log output.

```yaml
deploy:
   - foreach:
       var: host
       in: [ 'server1', 'server2' ]
       do:
           - ship [shipping to server ${host}]:
                 host: ${host}
                 from: local/path/file.txt
                 to: /tmp/remotepath/
```

#### Send a single file to a remote server

```yaml
do:
   # first we create a local file in /clarive/local/path/file.txt
   - write_file:
        file: local/path/file.txt
        body: hello world

   # now we ship local/* but remove the prefix 'local/'
   - ship:
       from: local/path/file.txt
       to: /tmp/remotepath/
       host: localhost
```

#### Send a whole directory to a remote server

```yaml
do:
   - mkdir -p mylocaldir/subdir
   - touch mylocaldir/subdir/my_file

   # now we ship local/* but remove the prefix 'local/'
   - ship:
       from: mylocaldir
       to: /tmp/remotepath/
       host: localhost
```

#### Send a relative directory to a remote server

```yaml
do:
   # first we create a local file in /clarive/local/path/file.txt
   - write_file:
        file: local/path/file.txt
        body: hello world

   # now we ship local/* but remove the prefix 'local/'
   - ship:
       from: local/
       anchor_path: local/
       to: /tmp/remotepath/
       host: localhost
       include:
          - \.txt$    # only files that end in \.txt
```

#### Import a module

```yaml
import:
   - .clarive/mymodule.yml
```

#### Joining an array into a string

```yaml
do:
   - users =:
       - user1
       - user2
   - echo: |
        {{ users.map( function(val){ return `<li>${val}</li>` }).join('\n')  }}
```

#### Using ES6/Babel in ClaJS

Using the Babel transpiler in handlebar templates:

```yaml
do:
   - foo =:
       - user1
       - user2
   - echo: |
        {{
            "use transpiler(babel)";
            foo.map( ( val ) => `<li>${val}</li>` ).join('\n')
        }}
```

And in a full ClaJS code block:

```javascript
do: |
   "use transpiler(babel)";

   class Builder {
       foo(x) {
           return `value=${x}`
       }
   }

   let obj = new Builder();
   print( obj.foo( 123 ) );
```

#### Publish a file to the job log

```yaml
build:
  - tar cvzf dist-files.tgz dist/
  - log:
       msg: build completed
       file: dist-files.tgz
```
#### Zip a directory

The `base` parameter is not required. By default
it's set to `/`, meaning it starts relative to `from`.


```yaml
do:
   - zip:
       from: /tmp/zzz/
       to: /tmp/rr.zip
       base: /
```

If you want to prepend a different base, just add it to `base`.

```yaml
do:
   - zip:
       from: /tmp/zzz/
       to: /tmp/rr.zip
       base: myprefix/this/dir
```

#### Zip a directory with a different timestamp

Sometimes you want to timestamp in a zip to a different
timestamp from what the system offers you. That
can be accomplished with the `time` option.

```yaml
do:
   - zip:
       from: /tmp/zzz/
       to: /tmp/rr.zip
       time: 2012-10-11 22:01:00
```

#### Tar a directory with relative path and timestamp

```yaml
do:
   - tar:
       from: /tmp/zzz/
       to: /tmp/mytar.tar
       base: /myprefix
       time: "2017-09-18 10:22:10"
```

#### Tar a directory including and excluding files

Includes are processed before exclude rules.  In the following, files or
directories that contain the string `file-` anywhere in its **full path** are
included, but files with the extension `.txt` are excluded.

The include/exclude pattern matching does not take into consideration the
`base` prefix.

```yaml
do:
   - tar:
       from: /tmp/zzz/
       to: /tmp/rr.tar
       include:
          - file-
       exclude:
          - \.txt
```

#### Parse a XML file into the stash

For this given XML file:

```xml
<xml>
  <somenode>
      hello world
  </somenode>
</xml>
```

We would parse it with this code:

```yaml
do:
   - parse_file:
        file: /path/to/file.xml
        type: xml
        returning: myvar
   - print: "Here we go: ${myvar.xml.somenode}"
```

#### Parse a XML file into the stash, removing the root node

The `KeepRoot` option removes the root node.

```yaml
do:
   - parse_file:
        file: /path/to/file.xml
        type: xml
        options:
           KeepRoot: 1
        returning: myvar
   - print: "Here we go: ${myvar.somenode}"   # note that the .xml part is not necessary anymore
```

#### Parse a YAML file into the stash

Given this input `file.yml`

```yaml
aa: 10
bb: 20
foo:
   - 12
   - 13
```

```yaml
do:
   - parse_file:
        file: /path/to/file.yml
        type: yaml
        returning: myvar
   - print: "Here are the ${myvar.value[1]} reasons why"   # ... 13 reasons why
```

#### Parse a INI file

```ini
foo=100
bar=200
log_file=/long/path/file.log
[temporary]
tmp_dir=/tmp
tmp_port=8787
```

Parse it with:

```yaml
do:
   - parse_file:
        file: /path/to/file.ini
        type: ini
        returning: myvar
   - echo: tmp_dir is ${myvar.temporary.tmp_dir}
```

#### Parse a Properties File

Here's a properties file straight out of the Wikipedia:

```properties
# You are reading the ".properties" entry.
! The exclamation mark can also mark text as comments.
# The key characters =, and : should be written with
# a preceding backslash to ensure that they are properly loaded.

# However, there is no need to preceede the value characters =, and : by a backslash.
website = https://en.wikipedia.org/
language = English

# The backslash below tells the application to continue reading
# the value onto the next line.
message = Welcome to \
          Wikipedia!

# Add spaces to the key
key\ with\ spaces = This is the value that could be looked up with the key "key with spaces".

# Unicode
tab : \u0009

# If you want your property to include a backslash, it should be escaped by another backslash
path=c:\\wiki\\templates

```

Parse it with:


```yaml
do:
   - parse_file:
        file: /path/to/file.properties
        type: properties
        returning: myprops
   - echo: tmp_dir is ${myprops.message}
```

#### Parse a JSON file

```json
{ "foo": [ { "bar": true } ] }
```

Can be parsed with the following rulebook:

```yaml
do:
   - parse:
        file: /tmp/tt/file.json
        type: json
        returning: aaa
   - echo: "true is ${aaa.foo[0].bar}"  # true is 1
```

#### Parse from a string instead of a file

The parsed content does not necessarily has to be stored in a file. It could
just come from a variable or a string passed as the `body` attribute.

```yaml
vars:
   - jsondata: |
        { "foo": [ { "bar": true } ] }
   - xml_content: |
        <xml>
           <foo name="beautiful" />
        </xml>
do:
   - parse:
        body: ${jsondata}
        type: json
        returning: json_parsed
   - parse:
        body: ${xml_content}
        type: xml
        returning: xml_parsed
   - echo: "XML is ${xml_parsed.xml.foo.name}"
```


#### Call a webservice and parse its JSON content
