ZFS on Linux on sacloud
=======================

# Description

Create ZOL server on sacloud

**Note: zol role is heavily inspired by [GR360RY/zfs-root-ansible](https://github.com/GR360RY/zfs-root-ansible)**

# Usage

## Install requirements

```bash
$ pip install -r requirements.txt
```

## Edit .envrc

Edit `.envrc` and enter your tokens.

```bash
$ cp -ipv .envrc.sample .envrc
$ $EDITOR .envrc
$ direnv allow
```

## Edit inventory file

```bash
$ cp -ipv hosts.yml.sample hosts.yml
$ $EDITOR hosts.yml
```

## Create ssh key

```bash
$ ssh-keygen -f keys/id_rsa
```

## Install sacloud library via ansible-galaxy

```bash
$ ansible-galaxy install -r install_roles.yml
```

## Bootstrapping

```bash
$ ansible-playbook -i ./bin/hosts.py site.yml --limit localhost --tags bootstrap -vvv
```

## Provisioning

```bash
$ ansible-playbook -i ./bin/hosts.py site.yml --limit tank -vvv
```

# License

MIT

# Author

[knakayama](https://github.com/knakayama)
