
# Kubernetes Cluster

## Description
This project is a simple way to create a kubernetes cluster using vagrant and ansible.

## Directory structure
```bash
.
├── README.md
├── Vagrantfile
├── ansible.cfg
├── inventory
│   └── hosts.ini
├── main.yaml
├── playbooks
│   ├── kubernetes-dependencies.yaml
│   ├── master-dependencies.yaml
│   ├── reset.yaml
│   ├── scale.yaml
│   └── worker-dependencies.yaml
├── requirements.txt
├── reset.yaml
└── scale.yaml

3 directories, 13 files
```

# How to use
1. Clone this repository
2. Run `vagrant up` to create the cluster
3. Run `vagrant ssh master` to access the master node
4. Run `kubectl get nodes` to check the nodes status
5. Run `kubectl get pods --all-namespaces` to check the pods status
