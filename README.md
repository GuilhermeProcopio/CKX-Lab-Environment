# CKX Lab Environment

A **Kubernetes lab environment** using **Vagrant**, **Ansible**, and **KVM/libvirt** for local development and testing.

---

## Overview

This project automates the creation of a lightweight Kubernetes cluster with:

- **1 Control Plane node** (3 GB RAM, 2 CPUs)  
- **2 Worker nodes** (2 GB RAM, 2 CPUs each)  
- **Containerd** as the container runtime  
- **Flannel** as the CNI plugin  


### Software Requirements
1. **Install KVM/QEMU and libvirt**
2. **Install Vagrant**
3. **Install the Vagrant libvirt plugin**
4. **Install Ansible**

### setuping the cluster 

```bash
ansible-playbook -i inventory. ini {path to playbooks}
```

after setup the cluster, use ```vagrant ssh control-plane``` to access or in your host:
```bash
    export KUBECONFIG=~/path/to/copied/kubeconfig
    kubectl get nodes
```

