
# Enver

  Stop pasting your hosts credentials from emails or Skype chats.
  Enver is a shell utility written in Node.js to store your accounts informations.
  You can retrieve any information saved with one command, copied in your clipboard, and safely not displayed in your shell.
  All saved data will be encrypted.

## Installation

Install enver using NPM (Requires Node v0.8.x or newer)

    $ npm install -g enver
    $ enver init

`init` creates the RSA keys that will be placed in ~/.enver

#Commands
###Import

    $ enver import path/to/json

You can easily import a json file. This will not erase your previously inserted data, accounts will merged.

#####json example

```js
{
    "projectname": {
        "ssh": {
            "user": "foo",
            "password": "bar"
        }
    }
}
```

The structure is completely flexible.

###Get

    $ enver get projectname.ssh.user
    
The retrieved key will be copied in your clipboard and won't be displayed.

###Delete

    $ enver delete projectname.ssh.user
    
###Add

    $ enver add newproject.db.user
    
After this command you will be prompted to insert the value of the object so it won't be present in your command history.

###List

    $ enver list [path]
    
This command will show the complete, or partial depending on the presence of [path], json structure without leaves keeping users and passwords hidden.

```bash
$ enver list
projectname
└ ssh
  └ user
  └ password

$ enver list projectname.ssh
user
password
```

###Export

    $ enver export path/to/file.json

This command exports the database in a clear json.
If you want to format it you may want to use [jsonlint for node](https://github.com/zaach/jsonlint).

## Oh My Zsh! autocomplete plugin

copy `~/node_modules/enver/enver.plugin.zsh` inside your `~/.oh-my-zsh/plugins/` and activate it in your `~/.zshrc` file to enable autocomplete for commands and object paths.

special thanks to [flevour](https://github.com/flevour)

## Links

 - [commander.js](http://visionmedia.github.com/commander.js/)
 - [jsonlint for node](https://github.com/zaach/jsonlint)
 - [nodejs extend](https://github.com/shimondoodkin/nodejs-clone-extend)
 - [AES](http://it.wikipedia.org/wiki/Advanced_Encryption_Standard)
 - [RSA](http://en.wikipedia.org/wiki/RSA_\(algorithm\))