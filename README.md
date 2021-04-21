# MOC Ansible

This is the foundation of our Ansible-managed infrastructure.

## Installing roles

The playbooks in this project depend on some external roles, defined
in [requirements.yml](requirements.yml). You can install them like
this:

```
ansible-galaxy install -r requirements.yml --role-path roles
```

If `version` in a requirement is set to `master`, Ansible can't tell
when there's been an update. You can force a re-install by adding the
`--force` option...

```
ansible-galaxy install -r requirements.yml --role-path roles --force
```

...although it's better to use specific references (tags, commit ids,
etc) in `requirements.yml`.


## Directory structure

The directory structure follows some of the guidlines described in the
[Sample Ansible setup][] documentation.

[sample ansible setup]: https://docs.ansible.com/ansible/latest/user_guide/sample_setup.html
