# Ansible

## Run Playbook

To run a Playbook

```
ansible-playbook -i <hosts file> <playbook.yml>
```

E.g.

```
ansible-playbook -i hosts docker.yml
```

## Dry Run

Dry run checks what changes will be made without applying any changes.

Add ```--check``` to the command. I.e.

```
ansible-playbook -i hosts docker.yml --check
```

## Single tag

If the actions in the playbook are tagged, then you can run only the items for a specific tag instead of the entire playbook.

To run a tag, add ```--tags <tagname>``` to the command. Run multiple tags separate them with a comma;```--tags tag1,tag2```

E.g.
```
ansible-playbook -i hosts docker.yml --tags docker
```