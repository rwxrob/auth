# Go Oauth2 Helper Module

*Canonical source at <https://github.com/rwxrob/auth-go>*

![Oauth2 Session](doc/session.gif)

[![GoDoc](https://godoc.org/github.com/rwxrob/auth-go?status.svg)](https://godoc.org/github.com/rwxrob/auth-go)
[![License](https://img.shields.io/badge/license-Apache-brightgreen.svg)](LICENSE)
[![Go Report
Card](https://goreportcard.com/badge/github.com/rwxrob/auth-go)](https://goreportcard.com/report/github.com/rwxrob/auth-go)
[![Coverage](https://gocover.io/_badge/github.com/rwxrob/auth-go)](https://gocover.io/github.com/rwxrob/auth-go)

Designed to help make command line Oauth2 easier to implement and use
from shell scripts and other command line utilities.

## Example Usage

### Main

```
auth <name>
auth token <name>
auth grant <name>
auth refresh <name>
auth help
```

### Create, Replace, Update, Delete (CRUD)

```
auth add
auth rm <name>
auth edit
auth export <file> [<name> ...]
auth import <file> [<name> ...]
```

### View / Output

```
auth ls
auth conf 
auth json <name>
auth get access <name>
auth get refresh <name>
auth get type <name>
auth get expiry <name>
auth get state <name>
auth get code <name>
auth get id <name>
auth get secret <name>
auth get scopes <name>
auth get redirecturl <name>
auth get authurl <name>
auth get tokenurl <name>
auth get style <name>
```

### Embed

```
curl -H "Authorization: Bearer $(auth <name>)" https://api.example.com/some
```

The `auth` command can be used in place of sensitive token and other
credential information within shell scripts. By default, the user will
be prompted when further authorization flow steps are needed, including
the opening of a local graphical web browser automatically. The level of
interaction can be isolated for scripts that must run without blocking
on waits for interactivity.

Unlike many other authorization solutions, `auth` starts a local web
server to handle the redirection and safely intercept the token that was
upgraded from the authorization code. Other tools generally prompt for
this to be cut and pasted in. If the opening of the web browser fails, a
prompt is shown instead.

## TODO

* Add Oauth 1.0a support (twitter)
* Add token revocation
* As much test coverage as we can achieve without a mock token server
* Add some detection of changes to the file since opened so don't
  overwrite with currently running process with the cache open (like vi)
