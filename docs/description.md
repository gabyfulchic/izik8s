# Scope 🔍  
  
This project is done in a school scope.  
It's for the Yday, a day where we can improve our knowledge and be inventive.  
  
# Description 📑  
  
**Organisation :**  
In a first step it will be a question of establishing the action plan in order to choose the solutions to package the kubernetes cluster. (Ansible, Vagrant etc...)
It will be necessary to compare the solutions, to see which are the most widespread, used and especially effective in our case of use.
It will therefore be necessary to make a trello as well as a visual roadmap if possible (logo, images etc...).
The project will surely have its Github repository in order to use the git version management software for scripts/configurations.

**Pre-requisites :**  
- Knowledge of K8S administration
- Docker knowledge
- Knowledge of open-source solutions around containers (https://landscape.cncf.io/)
- Knowledge of scripting (bash/python)
- Network/system knowledge (Virtualization, CNI, storage solution etc.)

**Main objective :**  
The goal will be to create a kubernetes cluster and to understand its eco-system by doing everything manually from A to Z.
The k8s cluster will have to be deployable in 1 or 2 commands. It will therefore be necessary to create the VMs (Kvm), install on the nodes the kubernete components according to their role (kubeapi-server, kube-scheduler, kubelet, kube-proxy, docker) as well as the storage and network solutions (CNI) allowing the containers to communicate and use persistent data for DBs for example.

**Optionnal objectives :**  
If I have time, here is a list of things to do to deepen each component of a container stack.  
- a way to **template/automate** the cluster deployment process to make it usable by a larger community *(even for people unfamiliar with the k8s ecosystem)*
- deployment of a **registry/artifacts** storage solution *(to store docker images, helm chart etc...)*
- the automation of the **renewa**l of Kubernetes **certificates** and root CA *(to help cluster administration)*
- the deployment of a **backup/restore** solution for the cluster's state. *(to help administration and increase confidence in the cluster)*

Then, if time allows it once again, the project will be extended to replicate it around the deployment of another solution of
orchestration and open-source container (**Hashicorp Nomad** and **Podman**).

The rating will be based on the progress of the project obviously (without taking into account the most optional ones)
The final goal of Yday is to package the deployment of a k8s cluster in vms (Qemu/KVM).

This Yday comes from my desire to become a CKA (Certified Kubernetes Administrator) to validate my skills and knowledge in the business world.
