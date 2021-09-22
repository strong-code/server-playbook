# server-playbook
Ansible playbook(s) to get my server just how I like it

# Task list
|Task|Description|Notes|
|---|---|---|
|[users](tasks/users.yml)|Sets up user accounts, groups, and permissions||
|[packages](tasks/packages.yml)|Desired package/PPA/bin inclusion/exclusion|Eventually, non-standard PPA installs will get too big for this file (e.g. `exa` or `asdf`). Should think about `subtasks/` dir|
|[dotfiles](tasks/dotfiles.yml)|Clones and symlinks the [dotfiles](https://github.com/strong-code/dotfiles) repo|Symlinks systemd service files, so this should always run before service install tasks|
|[docker](tasks/docker.yml)|Install Docker engine and supporting components|Responsible for shared Docker config such as `prom-grafana` bridge network|
|[irssi](tasks/irssi.yml)|Install irssi|`dotfiles` task will handle symlinking `~/.irssi` dir|
|[prometheus](tasks/prometheus/yml)|Install and configure Prometheus container and local `node_exporter`||
|[grafana](tasks/grafana.yml)|Install and configure Grafana container||
|[certbot](tasks/certbot.yml)|Install certbot and install nginx certs for `strongco.de` and `start.strongco.de`|Email and domains are hardcoded. Safely idempotent. `certbot renew` is handled by [crontab](https://github.com/strong-code/server-playbook/blob/main/tasks/dotfiles.yml#L77) from [dotfiles](https://github.com/strong-code/dotfiles)|

# Testing locally with Vagrant

Ansible will run with `local` connection as the Vagrant provisioner, so just 

    $ vagrant up

# Running against temp test server

Override remote host IP with 

    $ ansible-playbook main.yml --extra-vars "var_host=<ip>"

# DNS

DNS records are managed under iwantmyname.com with cloud firewall rules on DO 
