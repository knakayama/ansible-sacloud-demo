Building WordPress x Nginx on sacloud
=====================================

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

## Create ssh keys

```bash
$ ssh-keygen -f keys/id_rsa
```

## Install sacloud library via ansible-galaxy

```bash
$ ansible-galaxy install -r install_roles.yml
```

## Bootstrapping

```bash
$ ansible-playbook -i ./bin/hosts.py site.yml --limit localhost --ask-become-pass -vvv
```

## Provisioning

```bash
$ ansible-playbook -i ./bin/hosts.py site.yml --limit 'db,web' --skip-tags bootstrap --ask-become-pass -vvv
```
