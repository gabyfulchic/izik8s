# izik8s 🐈  
  
izik8s will target users who want to deploy and test some solutions around the k8s world  
on a multi-node cluster that you can self-host with virtual machines. For example you will be  
able to test solutions like [kube-bench](https://github.com/aquasecurity/kube-bench), [popeye](https://github.com/derailed/popeye), [k9s](https://github.com/derailed/k9s) or [haproxy-ingress](https://github.com/haproxytech/kubernetes-ingress) on cluster close to a  
prod-one if you simulate traffic for example with [gatling](https://github.com/gatling/gatling). You will never fear about testing a  
new tool on your company's Kubernetes Development cluster.  
  
## Links  
  
You can find a detailed description [here](description.md).  
And my personal objectives around this project [here](goal.md).  
Feel free to contact me if you want to contribute or discuss about the project : https://gitter.im/izik8s/community  

## Dependencies

* Vagrant 2.2.13
```bash
curl https://releases.hashicorp.com/vagrant/2.2.10/vagrant_2.2.13_linux_amd64.zip --output vagrant_2.2.10_linux_amd64.zip
unzip vagrant_2.2.13_linux_amd64.zip
```

* Virtualbox 6.0.6
```bash
https://www.virtualbox.org/wiki/Linux_Downloads
```

* Virtualbox Guest Additions 6.0.6 (for optimizations + shared folders etc...)
```bash
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://download.virtualbox.org/virtualbox/6.0.6/VBoxGuestAdditions_6.0.6.iso
sudo mkdir /media/VBoxGuestAdditions
sudo mount -o loop,ro VBoxGuestAdditions_6.0.6.iso /media/VBoxGuestAdditions
sudo sh /media/VBoxGuestAdditions/VBoxLinuxAdditions.run
rm VBoxGuestAdditions_6.0.6.iso
sudo umount /media/VBoxGuestAdditions
sudo rmdir /media/VBoxGuestAdditions
```

* Ansible 2.10.3  
```bash
pip install -r requirements.txt
```

## Deploy your cluster

* edit IPs' prefix according to your desires  
```bash
GNU # sed -i "s/ip_prefix = '10.33.0.'/ip_prefix = '192.168.1.'/g" Vagrantfile
BSD # sed -i "" -e "s/ip_prefix = '10.33.0.'/ip_prefix = '192.168.1.'/g" Vagrantfile
```

* Up your environment
```bash
vagrant up
```
