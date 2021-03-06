##### To install Vagrant CentOS ISO:

- CentOS 6.5:

```
vagrant box add centos-6 https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box
```

- CentOS 6.6:
  
```
vagrant box add box-cutter/centos66
```

---

##### To create VM:

```
cd ~/VirtualBox VMs/
mkdir CentOSTest
cd CentOSTest
vagrant init
```

Edit config file `/Users/<username>/VirtualBox VMs/CentOSTest/Vagrantfile` :

```
config.vm.box = "centos-66"
yum update
yum install nano 
```

---

##### To run VM:

```
vagrant up && vagrant ssh
sudo su
cd /vagrant
sudo halt
```

---

##### To see Mac's Downloads folder from inside VM:

Edit config file `/Users/<username>/VirtualBox VMs/CentOSTest/Vagrantfile` :

```
config.vm.synced_folder "/Users/<username>/Downloads", "/shared/downloads"
```

---


