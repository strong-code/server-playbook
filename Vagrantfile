Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.limit = 'local'
    ansible.inventory_path = 'inventory'
    ansible.playbook = 'main.yml'
  end
end
