Dans un premier temps il sera question d'établir le plan d'action afin de choisir les solutions pour packager le cluster kubernetes. (Ansible, Vagrant etc..)
Il faudra comparer les solutions, voir lesquelles sont les plus répandues, utilisées et surtout efficaces dans notre cas d'usage.
Il faudra donc réaliser un trello ainsi qu'une roadmap visuelle si possible (logo, images etc...).
Le projet aura surement son dépôt Github afin d'utiliser le logiciel de gestion de version git pour les scripts/configurations.

Les pré-requis :
- Connaissances K8S administration
- Connaissances Docker
- Connaissances des solutions open-source autour de la conteneurisation (https://landscape.cncf.io/)
- Connaissances en scripting (bash/python)
- Connaissances en réseau/système (Virtualisation, CNI, solution de stockage etc..)

Le but sera de créer un cluster kubernetes et d'apréhender son éco-système en faisant tout manuellement de A à Z.
Il faudra que le cluster k8s soit déployable en 1 ou 2 commandes. Il faudra donc créer les VM (Kvm), installer sur les noeuds les composants kubernetes suivant leur rôle (kubeapi-server, kube-scheduler, kubelet, kube-proxy, docker) ainsi que les solutions de stockage et de réseau (CNI) permettant aux conteneurs de communiquer et d'utiliser des données persistentes pour des DBs par exemple.

Plus :
Si j'ai le temps, voici une liste des choses à faire (optionnelles) pour apronfondir chaque composant d'une stack autour de la conteneurisation.
- le déploiement d'une solution de registry/stockage d'artifacts (pour stocker les images docker, helm chart etc..)
- l'automatisation du renouvellement des certificats Kubernetes et du root CA (pour aider l'administration du cluster)
- le déploiement d'une solution de sauvegarde/restauration de l'état du cluster. (pour aider l'administration et augmenter la confiance envers le cluster)
- un moyen de templater le script de déploiement du cluster afin de le rendre utilisable par une plus large communauté (même pour les gens ne connaissant pas l'écosystème k8s)

Ensuite, si le temps le permet encore une fois, il sera question d'élargir le projet afin de le reproduire autour du déploiement d'une autre solution d'
orchestration et de conteneurisation open-source (Hashicorp Nomad, Podman).

La notation sera basée sur l'avancement du projet évidemment (sans prendre en compte les plus optionnels)
Le but final du Yday étant de packager le déploiement d'un cluster k8s dans des vms (Qemu/KVM)

Ce Yday me vient de mon envie d'être certifié CKA (Certified Kubernetes Administrator) pour valider mes compétences et connaissances dans le monde de l'entreprise.
