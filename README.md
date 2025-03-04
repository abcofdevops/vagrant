# Vagrant
Create your own linux machines using Vagrant

# To get IPs of newly created machines
for machine in $(ls -1 .vagrant/machines); do ip=$(vagrant ssh $machine -c "ip -4 -o addr show eth0 | awk '{print \$4}' | cut -d'/' -f1" 2>/dev/null | tr -d '\r'); echo $ip $machine ; done
