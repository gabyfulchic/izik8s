# Kernel modules, sysctl confs, swapoff, fw rules
swapoff -a
sudo modprobe br_filter
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sudo sysctl --system
sudo firewall-cmd --add-port 10250/tcp --permanent
sudo firewall-cmd --add-port 30000-32767/tcp --permanent
sudo firewall-cmd reload

# CRI containerd
sudo modprobe overlay
cat <<EOF | sudo tee /etc/sysctl.d/99-kubernetes-cri.conf
net.bridge.bridge-nf-call-iptables  = 1
net.ipv4.ip_forward                 = 1
net.bridge.bridge-nf-call-ip6tables = 1
EOF
sudo sysctl --system
sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-commoncurl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key --keyring /etc/apt/trusted.gpg.d/docker.gpg add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
sudo apt-get update && sudo apt-get install -y containerd.io
sudo mkdir -p /etc/containerd
containerd config default | sudo tee /etc/containerd/config.toml
sudo systemctl restart containerd
https://kubernetes.io/docs/setup/production-environment/container-runtimes/#containerd-systemd

# Kubeadm
sudo apt-get update && sudo apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl

https://kubernetes.io/fr/docs/setup/production-environment/tools/kubeadm/install-kubeadm/#configurer-le-driver-de-cgroup-utilis%C3%A9-par-la-kubelet-sur-un-n%C5%93ud-master 
sudo systmctl daemon-reload
sudo systemctl restart kubelet

# Node joining cluster
kubeadm join (the one saved in the output from `kubeadm init`)


