Vagrant.configure(2) do |config|
  config.vm.box "geerlingguy/ubuntu2004"

  config.vm.provision "ansible_local" do |ansible|
    ansible.limit = 'local'
    ansible.inventory_path = 'inventory'
    ansible.playbook = 'local.yml'
  end
end
