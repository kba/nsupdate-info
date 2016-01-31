update-nsupdate
---------------

Perl script to update a [nsupdate.info](https://nsupdate.info) DynDNS.

* [Requirements](#requirements)
* [Installation](#installation)
  * [Without git](#without-git)
  * [With git](#without-git)
* [Usage](#usage)
* [Options](#options)
  * [`--user`](#--user)
  * [`--password`](#--password)
  * [`--force`](#--force)
* [Commands](#commands)
  * [`ipv4`](#ipv4)
  * [`ipv6`](#ipv6)
  * [`makeconfig`](#makeconfig)
  * [`crontab`](#crontab)
* [License](#license)

## Requirements

* Perl
* curl

## Installation

Copy
[`nsupdate-info`](https://raw.githubusercontent.com/kba/nsupdate-info/master/nsupdate-info)
into the `bin` folder of your home directory.

### Without Git

```
mkdir -p ~/bin
cd ~/bin
wget https://raw.githubusercontent.com/kba/nsupdate-info/master/nsupdate-info
chmod a+x nsupdate-info
```

### With Git

```
mkdir -p ~/bin
git clone https://github.com/kba/nsupdate-info
cd nsupdate-info
cp nsupdate-info ~/bin
```

## Usage

```
nsupdate-info <ipv4|ipv6|makeconfig|crontab> --user=<user> --password=<password> [--force=1]
```

First, you need to register for an account on [nsupdate.info]() and add a host.
Remember to copy your secret token (i.e. password for that host).

You can pass options on the command line or persist them into a config file.

To create a config file, specify the options on the command line and use the
`makeconfig` subcommand.

## Options

### --user

**REQUIRED** unless set in config file.

The hostname to redirect from.

### --password

**REQUIRED** unless set in config file.

The secret token for the host.

### --force

Specify `--force=1` to force an update of a host even if the cached IP is still
up-to-date.

## Commands

### ipv4

Set the host to redirect to the external IPv4 IP address.

### ipv6

Set the host to redirect to the external IPv6 IP address.

### makeconfig

```
nsupdate-info makeconfig --user=USERNAME --password=PASSWORD
```

Create a config file `~/.config/nsupdate-info/config.ini` that contains user/passsword.

**ATTENTION:** Will overwrite if it exists.

### crontab

Prints a snippet ready for adding to your crontab.

## License

MIT licensed

(c) 2016 Konstantin Baierer
