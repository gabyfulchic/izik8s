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

* Ansible  
```bash
pip install -r requirements.txt
```

* Vagrant-libvirt  
[Vagrantfile](Vagrantfile)

* KVM
```bash
sudo apt-get install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
```

* Vagrant
```bash
curl https://releases.hashicorp.com/vagrant/2.2.10/vagrant_2.2.13_linux_amd64.zip --output vagrant_2.2.10_linux_amd64.zip
unzip vagrant_2.2.13_linux_amd64.zip
```

## Deploy your cluster

* edit IPs' prefix according to your desires  
```bash
GNU # sed -i "s/ip_prefix = '10.33.0.'/ip_prefix = '192.168.1.'/g" Vagrantfile
BSD # sed -i "" -e "s/ip_prefix = '10.33.0.'/ip_prefix = '192.168.1.'/g" Vagrantfile
```

* Up your environment
```bash
! WORKAROUND ! https://github.com/vagrant-libvirt/vagrant-libvirt#using-docker-based-installation
docker run -it --rm \
  -e LIBVIRT_DEFAULT_URI \
  -v /var/run/libvirt/:/var/run/libvirt/ \
  -v ~/.vagrant.d:/.vagrant.d \
  -v $(pwd):$(pwd) \
  -w $(pwd) \
  vagrantlibvirt/vagrant-libvirt:latest \
    vagrant up
```
