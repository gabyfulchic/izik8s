# UP/DOWN kvm services on your host

It will help you to free some ressources on your host when you switch from your kubernetes
tests to your usual activities.

## UP
```bash
sudo systemctl start qemu-kvm.service
sudo systemctl start libvirtd.service
sudo systemctl start libvirt-guests.service
sudo systemctl enable libvirtd.service
sudo systemctl enable libvirt-guests.service
sudo systemctl enable qemu-kvm.service
```

## DOWN
```bash
sudo systemctl stop qemu-kvm.service
sudo systemctl stop libvirtd.service
sudo systemctl stop libvirt-guests.service
sudo systemctl disable libvirtd.service
sudo systemctl disable libvirt-guests.service
sudo systemctl disable qemu-kvm.service
```

## CHECK STATUS
```bash
sudo systemctl status qemu-kvm.service
sudo systemctl status libvirtd.service
sudo systemctl status libvirt-guests.service
```

