# Dapr on K3S
This repository contains an Ansible playbook that installs the following on the local computer and in a K3S cluster:<br/>
- Dapr CLI on the local computer
- Dapr in K3S
- Dapr state store and pub/sub backed by Redis

More information on Dapr: https://dapr.io/

## Install
Install using:<br/>
```ansible-playbook install-dapr.yml```

After the installation has completed, view the Dapr dashboard in a browser using the following command:<br/>
```dapr dashboard -k```

## Prerequisites
Ansible shall be installed on the local computer.<br/>
A K3S cluster, preferably as installed using https://github.com/krizsan/k3s-cluster-ansible,
and kubectl configured as to control the K3S cluster as default, which can be obtained using the kubectl-local-config.yml
Ansible playbook from the same repository.