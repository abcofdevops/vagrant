# Vagrant
**Create your own linux machines using Vagrant.**

>Vagrant is a tool used for building and maintaining virtualized development environments. It allows developers to create, configure, and manage virtual machines (VMs) using simple and repeatable workflows.


## Install Vagrant:
To use Vagrant, you first need to install it along with a virtualization provider (e.g., VirtualBox). You can download and install Vagrant from the official website:

[Vagrant Installation](https://developer.hashicorp.com/vagrant/docs/installation)

---

## Run VM's using vagrant file
>Vagrantfile in this repo is configured to run 3 VM's with ubuntu-20.04 distribution.  
>To change no of VM's edit vagrantfile > NUM_NODE  
>TO change Linux distribution edit vagrantfile > config.vm.box  

**Clone this repo [abcofdevops/vagrant.git](https://github.com/abcofdevops/vagrant.git)**

```bash
git clone https://github.com/abcofdevops/vagrant.git
```

  ```bash
  cd vagrant
  ```

**Start the VM's**
```bash
vagrant up
```

**To get IPs of newly created machines**   
-*Not required unless you need to connect to these VM's outside vagrant*

```bash
for machine in $(ls -1 .vagrant/machines); do \
ip=$(vagrant ssh $machine -c "ip -4 -o addr show eth0 | awk '{print \$4}' | cut -d'/' -f1" 2>/dev/null | tr -d '\r'); \
echo $ip $machine ; \
done
```

**SSH into the VM**

```bash
vagrant ssh vm01
```

**To Restart, stop or delete the VM**

```bash
\\ Restart VM and applies config changes
vagrant reload

\\ Stop VM [equilant to shut down] and user data is not deleted
vagrant halt

\\ Completely remove the VM and delete all data
vagrant destroy
```

**TO check or add box/VM image**

```bash
vagrant box list
vagrant box add 
```
---

**Bonus**   
To create your own vagrantfile

```bash
vagrant init
```
*Initializes a new Vagrant environment with a default Vagrantfile*

---
