# K8S ansible role

This is a Ansible role to prepare K8S cluster environment.

## Requirements

Ansible 2.9

## Default variables

|Variable|Value|Description|
|---|---|---|
```KUBE_GPG_URL```|<https://packages.cloud.google.com/apt/doc/apt-key.gpg>|
```KUBE_GPG_PATH```|/usr/share/keyrings/kubernetes-archive-keyring.gpg|
```KUBE_VERSION```|1.26.6-00|

## Example

```yaml
### create the requirements.yml
- src: git+https://github.com/willyhutw/ansible-role-k8s-preset.git
  name: k8s-preset

### install role
ansible-galaxy install -r requirements.yml -p ./roles

### create the playbook.yml
- hosts: all
  become: yes
  gather_facts: yes
  roles:
    - roles/k8s-preset

### run it!
ansible-playbook -i '192.168.56.11,192.168.56.12,192.168.56.13,' playbook.yml -e ansible_ssh_user=vagrant
```
