# Dapr on K3S
This repository contains an Ansible playbook that installs the following on the local computer and in a K3S cluster:<br/>
- Dapr CLI on the local computer
- Dapr in K3S
- Dapr state store and pub/sub backed by Redis

More information on Dapr: https://dapr.io/

## Prerequisites
The following are required to be able to use the playbook in this repository:

- Ansible installed on the local computer.<br/>
- A K3S cluster, preferably as installed using https://github.com/krizsan/k3s-cluster-ansible <br/>
- kubectl configured as to control the K3S cluster as default.
<br/>Can be obtained using the ```kubectl-local-config.yml``` Ansible playbook from the same repository.

## Install
Install using:<br/>
```ansible-playbook install-dapr.yml```

## View Dapr Components
Having installed Dapr and the state store and pub/sub components, the Dapr CLI can be used to list the components known to Dapr:<br/>
```dapr components -k```

## Dapr Dashboard
With Dapr installed, the Dapr dashboard can be viewed in a browser using the following command:<br/>
```dapr dashboard -k```
