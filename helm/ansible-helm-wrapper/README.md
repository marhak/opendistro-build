# Ansible wrapper for deploying opendistro-for-elasticsearch

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Ansible wrapper for deploying opendistro-for-elasticsearch](#ansible-wrapper-for-deploying-opendistro-for-elasticsearch)
	- [Overview](#overview)
	- [Install ansible and required python addons](#install-ansible-and-required-python-addons)
	- [Fill inventory for your opendistro-for-elasticsearch backend](#fill-inventory-for-your-opendistro-for-elasticsearch-backend)
	- [Deploy the odfe cluster according the inventory definition](#deploy-the-odfe-cluster-according-the-inventory-definition)
		- [Generate certificates and append to cluster namespace secrets](#generate-certificates-and-append-to-cluster-namespace-secrets)
		- [Template the security configs and push to cluster namespace secrets](#template-the-security-configs-and-push-to-cluster-namespace-secrets)
		- [Template custom values according the inventory and Deploy the opendistro cluster](#template-custom-values-according-the-inventory-and-deploy-the-opendistro-cluster)
		- [Init the security index](#init-the-security-index)

<!-- /TOC -->

---

`NOTE: This is under development`

## Overview
Another way deploying the opendistro-for-elasticsearch cluster to Kubernetes.
This wrapper addition can be used to:
- deploying certs
- security configs
- deploying the odfe cluster by wrapping over the community provided Helm Chart

The credentials, cluster definition inventory and the secrets are stored to
path outside the repo choosed by the person doing the deployment.

## Install ansible and required python addons

```bash
FILL ME
```

## Fill inventory for your opendistro-for-elasticsearch backend

```bash
FILL ME
```

## Deploy the odfe cluster according the inventory definition

### Generate certificates and append to cluster namespace secrets
* [1-certs-to-odfe-kube-cluster.yml](./1-certs-to-odfe-kube-cluster.yml)

```bash
cd /path/to/ansible-helm-wrapper
ansible-playbook -i /path/to/your/odfe-<inventory>.hosts 1-certs-to-odfe-kube-cluster.yml --ask-vault-pass
```

### Template the security configs and push to cluster namespace secrets
* [2-append-configs-to-cluster.yml](./2-append-configs-to-cluster.yml)

```bash
cd /path/to/ansible-helm-wrapper
ansible-playbook -i /path/to/your/odfe-<inventory>.hosts 2-append-configs-to-cluster.yml --ask-vault-pass
```

### Template custom values according the inventory and Deploy the opendistro cluster
* [3-opendistro-cluster-deploy.yml](./3-opendistro-cluster-deploy.yml)

```bash
cd /path/to/ansible-helm-wrapper
ansible-playbook -i /path/to/your/odfe-<inventory>.hosts 3-opendistro-cluster-deploy.yml --ask-vault-pass
```

### Init the security index
* [4-init-odfe-security-index.yml](./4-init-odfe-security-index.yml)

```bash
cd /path/to/ansible-helm-wrapper
ansible-playbook -i /path/to/your/odfe-<inventory>.hosts 4-init-odfe-security-index.yml --ask-vault-pass
```
