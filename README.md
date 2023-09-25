# Build a PDI cluster via Ansible
Using Ansible, you can create a ETL cluster with Pentaho Data Integration.

## Files
- inventory
- collections
- roles
- site.yml
- reset.yml

## System requirements

Deployment environment must have Ansible 2.4.0+
Master and nodes must have passwordless SSH access

## Usage
First create a new directory based on the `sample` directory within the `inventory` directory:

```bash
cp -R inventory/sample inventory/my-cluster
```

Second, edit `inventory/my-cluster/hosts.ini` to match the system information gathered above. For example:

```bash
[pdi_v4]
xxx.xxx.xxx.xxx

[pdi_v7]
xxx.xxx.xxx.[xxx-yyy]

[pdi_v9]
xxx.xxx.xxx.[xxx-yyy]

[pdi_cluster:children]
pdi_v4
pdi_v5
pdi_v9
```

If needed, you can also edit `inventory/my-cluster/group_vars/all.yml` to match your environment.

Start provisioning of the cluster using the following command:

```bash
ansible-playbook site.yml -i inventory/my-cluster/hosts.ini
```

## Installer Ansible
```shell
pyenv virtualenv ansible
pyenv activate ansible
pip install ansible-core
```

## Create a container for ansible testing
```shell
cd test
docker-compose up -d
```
