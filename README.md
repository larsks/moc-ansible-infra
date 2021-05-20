# MOC Ansible

This is the foundation of our Ansible-managed infrastructure.

## Installing roles

The playbooks in this project depend on some external roles, defined
in [requirements.yml](requirements.yml). You can install them like
this:

```
ansible-galaxy install -r requirements.yml --roles-path roles
```

If `version` in a requirement is set to `master`, Ansible can't tell
when there's been an update. You can force a re-install by adding the
`--force` option...

```
ansible-galaxy install -r requirements.yml --roles-path roles --force
```

...although it's better to use specific references (tags, commit ids,
etc) in `requirements.yml`.

## Running the playbooks

You will first need to point Ansible at an inventory file. If you have
checked [moc-inventory-prod][] into the parent of the current
directory, you can set the `ANSIBLE_INVENTORY` environment variable
like this:

```
export ANSIBLE_INVENTORY=../moc-inventory-prod
```

Once you've set `ANSIBLE_INVENTORY`, you can run the `site.yml`
playbook:

```
ansible-playbook site.yml
```

You can limit execution to a specific host (or host group) using `-l`:

```
ansible-playbook site.yml -l example.massopen.cloud
```

You can limit execution to a specific role using tags (the `auto_tags`
plugin generates tags for each role):

```
ansible-playbook site.yml -t moc_firewall
```

[moc-inventory-prod]: https://github.com/CCI-MOC/moc-inventory-prod/

## Directory structure

The directory structure follows some of the guidlines described in the
[Sample Ansible setup][] documentation.

[sample ansible setup]: https://docs.ansible.com/ansible/latest/user_guide/sample_setup.html
