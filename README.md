# server-playbook
Ansible playbook(s) to get my server just how I like it

# Testing locally with Vagrant

Ansible will run with `local` connection as the Vagrant provisioner, so just 

    $ vagrant up

# Running against temp test server

Override remote host IP with 

    $ ansible-playbook main.yml --extra-vars "var_host=<ip>"

# DNS

DNS records are managed under iwantmyname.com with cloud firewall rules on DO 
