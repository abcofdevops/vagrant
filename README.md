# Vagrant
Create your own linux machines using Vagrant

# To get IPs of newly created machines
for machine in $(ls -1 .vagrant/machines); do ip=$(vagrant ssh $machine -c "ip -4 addr show eth0 | awk '/inet / {print \$2}' | cut -d'/' -f1"); echo $machine $ip ; done
