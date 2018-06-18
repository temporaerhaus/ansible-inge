ansible for vsh: inge
====================

This is a set of ansible roles used for the server inge in the [verschwoerhaus](https://verschwoerhaus.de).
It handles the radius requests from the wifi access points and provides the ldap.

### Usage
First, you need the ansible galaxy roles. Install them with:

```
ansible-galaxy install -r requirements.yml
```

If neccessary, change the ip in the `hosts` file. Put the vault password in the `vault` file.

Run ansible:

```
ansible-playbook --vault-password-file ./vault -i hosts --become --become-method=sudo --ask-become-pass playbook.yml
```

### Usage (test)
For testing locally if the roles do that stuff you want, we've included an `Vagrantfile`.
Execute `vagrant up`. If you changed something, use `vagrant provision`.

### Dev

To add new secret variables, put the vault password in the file `vault`, then for the variable `radius_client_secret` with the value `totallysecretvaluehere` encrypt it like this:

```
ansible-vault encrypt_string --vault-id ./vault 'totallysecretvaluehere' --name 'radius_client_secret'
```