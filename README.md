# Dapr on K3S

Installs the following:<br/>
- Dapr CLI on the local computer
- Dapr in K3S
- Dapr state store and pub/sub backed by Redis


More information on Dapr: https://dapr.io/

## Prerequisites
A K3S cluster, preferably as installed using https://github.com/krizsan/k3s-cluster-ansible,
and kubectl configured as to control the K3S cluster as default, which can be obtained using the kubectl-local-config.yml
Ansible playbook from the same repository.