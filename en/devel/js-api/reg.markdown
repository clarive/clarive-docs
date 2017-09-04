---
title: cla/reg - Registry Manipulation
index: 5000
icon: page
---

The Clarive registry holds extension points to many parts of the system, both client and server.

These functions are mostly useful in `init/` plugin entrypoints to register items like palette operations (services),
menu entries, events and others.

### cla.register()

Creates a registry entry in Clarive.

In the following example, we will reate a new menu entry.

```javascript
var reg = require('cla/reg');
reg.register('menu.admin.test',{ name: 'Test Menu', url: '/comp/testmenu.js' });
```

### cla.launch(key,opts)

Launches a registry service.

```javascript
var reg = require('cla/reg');
reg.register('service.test',{
    name: 'Foo Service',
    handler: function(){ return 99 }
});

reg.launch('service.test', { name: 'just trying this out', config: { foo: 'bar' } });
```

Options:

- `config` - a config object to be sent to the handler.
- `name` - reports the op name so that its logging information is more descriptive.
- `dataKey` - reports the op name so that its logging information is more descriptive.
- `stash` - an alternative stash; defaults to the current stash.

### Examples of execution of services.

In order to execute services within plugins, you need to know which variables have to be passed to them in order for
them to function correctly.

Any palette item may be called from a plugin, thus keeping everything more compact.

Among the items that may be called are: Launching remote scripts, shipping files via SSH, creation of Topics, etc.

Below are a number of examples of palette items that may be called, along with the variables needed for these. Not all
variables are needed in every case, but we have listed here all those that may be used.

### Executing remote commands (service.scripting.remote):

This is the service responsible for executing commands remotely.

```javascript
reg.launch('service.scripting.remote', {
    name: 'Remote launch', // Name of the task to be executed
    config: {
        errors: 'fail', // Type of errors to be monitored
        server: '1234', // Server ID on which it will be executed
        user: 'clarive', // User for connecting to the server
        path: 'ls -l', // Command we wish to launch
        output_error: '', // Regular expressions for monitoring errors
        output_warn: '', // Regular expressions for monitoring errors
        output_capture: '', // Regular expressions for monitoring errors
        output_ok: '', // Regular expressions for monitoring errors
        meta: {foor: bar}, // Metadata of the service where it is executed
        rc_ok: '200', // rc Ok code for monitoring errors
        rc_error: '404', // rc Error code for monitoring errors
        rc_warn: '302' // rc Warn code for monitoring errors
    }
});
```

### Shipping files remotely (service.fileman.ship)

Service responsible for shipping files remotely to another server.

```javascript
reg.launch('service.fileman.ship', {
    name: 'Remote ship', // Name of the task to be executed
    config: {
        server: '1234', // Server ID to which the file is to be shipped
        user: 'clarive', // User for connecting to the server
        recursive: "0", // Perform the operation recursively or not
        local_mode: "local_files", // Mode for shipping local files
        local_path: "/Home/", // Path to the file to be shipped
        remote_path: "/tmp/", // Directory of the remote server to which we would like to ship the file
        exist_mode_local: "skip", // Action mode when file not found
        rel_path: "file_only", // Shipping mode only for files or retaining the job path
        exist_mode: "reship", // Action mode when files have already been shipped by the job
        backup_mode: "none", // File backup mode
        rollback_mode: "none", // Rollback mode
        track_mode: "none", // File tracking mode
        audit_tracked: "none", // File audit mode
        chown: "", // chown permissions
        chmod: "", // chmod permissions
        max_transfer_chunk_size: "", // Maximum transfer size
        copy_attrs: "0" // Copy file attributes
    }
});
```

### Change in Topic Status (service.topic.change_status)

Service used for changing the Topic Status in Clarive.

```javascript
reg.launch('service.topic.change_status', {
    name: 'Change topic status', // Name of the task to be executed
    config: {
        topics: '123', // ID of the Topic we would like to change
        old_status: '3', // ID of the status from which the Topic is to be changed
        new_status: '4', // ID of the new Status we would like to assign to the Topic
        username: 'clarive'// User to which the change in Status is to be assigned
    }
});
```

### Creation of Topics ('service.topic.create')

Service used for creating Topics in Clarive.

```javascript
reg.launch('service.topic.create', {
    name: 'Create topic', // Name of the task to be executed
    config: {
        title: 'Topic title', // Title of the Topic that will be created
        category: '34', // ID of the category to which the Topic belongs
        status: '3', // ID of the Initial Status with which it is created
        username: 'clarive', // User to which creation of the Topic is assigned
        variables: {desc: 'hello'} // The different variables or fields inherent to the Topic to be created
    }
});
```

### Topic Update ('service.topic.update')

Service used for updating Topic content in Clarive.

```javascript
reg.launch('service.topic.update', {
        name: 'Update topic', // Name of the task to be executed
        config: {
        mid: '123', // ID of the Topic we would like to change
        username: 'clarive', // User to which Topic creation is assigned
        variables: {desc: 'hello'} // The different variables or fields inherent to the Topic to be updated
    }
});
```

### Deleting Topics ('service.topic.delete')

Service used for deleting Topics in Clarive.

```javascript
reg.launch('service.topic.delete', {
    name: 'Delete topic', // Name of the task to be executed
    config: {
        topics: '123', // ID of the Topic we wish to change
        username: 'clarive' // User to which Topic creation is assigned
    }
});
```
