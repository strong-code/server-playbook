Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "shell", run: "always" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = "echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys"
    s.inline = "chmod 700 ~/.ssh"
  end

  config.ssh.insert_key = false
  config.ssh.private_key_path = '/Users/chl/.ssh/id_rsa'
  config.ssh.forward_agent = true

  config.vm.provision "ansible" do |ansible|
    ansible.limit = 'local'
    ansible.inventory_path = 'inventory'
    ansible.playbook = 'main.yml'
    ansible.extra_vars = {var_host: "localhost"}
    ansible.raw_ssh_args = ['-o StrictHostKeyChecking=no', '-o ForwardAgent=yes']
  end

end
