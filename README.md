# Dapr on K3S
This repository contains an Ansible playbook that installs the following on the local computer and in a K3S cluster:<br/>
- Dapr CLI on the local computer
- Dapr services in K3S
- Dapr state store and pub/sub backed by Redis in K3S

More information on Dapr: https://dapr.io/
<br/><br/>
<b>Important!</b><br/>
Dapr, Redis and any applications using Dapr must reside in one and the same namespace in Kubernetes.<br/>
Otherwise, Dapr and applications using Dapr will not be able to establish contact with Redis.

## Prerequisites
The following are required to be able to use the playbook in this repository:

- Ansible installed on the local computer.<br/>
- A K3S cluster, as installed using https://github.com/krizsan/k3s-cluster-ansible or created using K3D.<br/>
  With K3D, a cluster can be created using the following command:
```bash
k3d cluster create -s 1 -a 3
```
- kubectl configured as to control the K3S cluster as default.
<br/>Can be accomplished using the ```kubectl-local-config.yml``` Ansible playbook from the https://github.com/krizsan/k3s-cluster-ansible repository.
<br/>K3D automatically configures kubectl when creating a new cluster.

## Install
Install using:<br/>
```bash
ansible-playbook install-dapr.yml
```

When run, the playbook will ask for a namespace in which to install Dapr and associated components. This namespace will be created if it does not already exist.<br/>
The namespace will be made the default namespace by the playbook.
### Verify Installation
To verify the Dapr installation, use the following command:<br/>
```bash
dapr status -k
```
All the Dapr services, i.e. dapr-operator, dapr-sidecar-injector, dapr-dashboard etc., should be healthy and have the status Running.

### View Dapr Components
Having installed the Dapr state store and pub/sub components, the Dapr CLI can be used to list the components known to Dapr:<br/>
```bash
dapr components -k
```

### Dapr Dashboard
With Dapr installed, the Dapr dashboard can be viewed in a browser using the following command:<br/>
Note: Change namespace to the namespace in which Dapr was installed.<br/>
```bash
dapr dashboard -k -n development
```

## Redis stack
In addition to installing Redis as state store and pub/sub for Dapr, the entire Redis stack is installed into the K3S cluster.<br/>
To view the Redis stack web UI, execute the following command in a terminal windows:<br/>
```bash
kubectl port-forward -n development svc/redis-stack 8001:8001
```
<br/>Then open the URL below in a browser on the same computer as the kubectl command above is executed:<br/>
```
http://localhost:8001
```

For additional information on the Redis stack, please refer to: https://redis.io/docs/about/about-stack/