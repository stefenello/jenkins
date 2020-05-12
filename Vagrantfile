Vagrant.configure(2) do |config|
    config.vm.box = "centos/7"
   
    #Habilitar el reenvio de puerto SSH
    config.vm.network "forwarded_port", guest: 22, host:2222, id: "ssh", auto_correct: true
   
    #Habilitar el reenvio de puerto Apache
    config.vm.network "forwarded_port", guest: 80, host:8080, id: "apache", auto_correct: true
   
    #Creacion de la VM en Virtualbox
    config.vm.define "jenkins" do |jenkins|
      jenkins.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "staging"
        ansible.verbose = 'vvv'
        ansible.playbook = "site.yml"
      end
    
    #Ampliacion de la memoria de la VM
      config.vm.provider "virtualbox" do |v|
        v.memory = 2048
      end
    end
  end