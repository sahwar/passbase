Passbase
========

Passbase is a free password manager built on [Keybase](https://keybase.io).

Generate long, random, secure passwords and store encrypted copies of them on your Keybase File System.

Soon, you'll also be able to share passwords with other Keybase users, at your discretion.

Usage
-----

**Whenever you create/change/read a password, it will open in `less`: this is to ensure it does not pollute your history, or remain visible on screen; once you have copied the password to your clipboard, press `q` to quit.**

Create a new password for cool-new-website:
```sh
passbase create cool-new-website
```

(Realise cool-new-website requires passwords to be at most 25 characters, and only contain the special characters `!` and `@`):
```sh
passbase change cool-new-website -n25 -S!@
```

Some time later, when you want to login to cool-new-website again:
```sh
passbase read cool-new-website
```

Get bored of cool-new-website:
```sh
passbase delete cool-new-website
```

What sites do we have passwords for again?
```sh
passbase list
```

### Aliases

You can also use `ls` and `rm` as aliases for the obvious.

`--length` and `-n` are synonyms; as are `--specials` and `-S`.

You can specify not to use any special characters at all with `--no-specials` or `-x`. (cf. [Defaults](#defaults))

### Defaults

The default password length is `128` characters. This is not for any particular reason - if you're copy-pasting the length is rather immaterial, and it's rarely caused me any issues. That said, I'm definitely open to feedback; if you're frequently running into lower limits, please open an issue (if one doesn't exist).

Special characters included by default are ``~`!@£&*_+-=\,./|?`` - specified  characters may only be a subset of these. They were arrived at by being those on my keyboard that do not break 'double-tap copy'. Again, open to suggestions for changes.

Upcoming Features
-----------------

Keybase allows not only keeping things private, but also mutual privacy. The main goal of v0.2 will be to facilitate *shared passwords* - like the supermarket or pizza place you order from with roommates, or the video on demand subscription you share with family.

Installation
------------

macOS users can use [Homebrew](http://brew.sh/):
```sh
brew install OJFord/formulae/passbase
```

or download [the latest release](https://github.com/OJFord/passbase/releases).

If you're building from source, you'll need Rust nightly (around November 2016 should be fine). PRs with easier installation on \$YOUR_PLATFORM are most welcome!

Development
-----------
[![CI Status](https://travis-ci.com/OJFord/passbase.svg?token=SxsettpUmvjPeVFxsTig&branch=master)](https://travis-ci.com/OJFord/passbase)

### Tests

The (integration) tests run inside a Docker container, primarily for ease of mocking the Keybase CLI tool and root directory.

``` {.sh}
$ docker-compose run tests
```
