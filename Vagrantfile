# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "genericfedora28" do |config|
    config.vm.hostname = "genericfedora28"
    config.vm.box = "generic/fedora28"
    config.vm.box_check_update = false

    config.vm.provider "virtualbox" do |vb|
      vb.gui = true 
      vb.memory = "16384"
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      vb.customize ["modifyvm", :id, "--draganddrop", "bidirectional"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]
      vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    end
  end
  
  config.vm.provision "shell", inline: <<-SHELL
  
    
    sudo echo "LANG=en_US.UTF-8" >> /etc/environment
    sudo echo "LANGUAGE=en_US.UTF-8" >> /etc/environment
    sudo echo "LC_ALL=en_US.UTF-8" >> /etc/environment
    sudo echo "LC_CTYPE=en_US.UTF-8" >> /etc/environment

    sudo dnf -y group install "Cinnamon Desktop"
    echo "exec /usr/bin/cinnamon-session" >> ~/.xinitrc

    #sudo dnf config-manager --add-repo ppa:webupd8team/java

    #wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.rpm"
    sudo dnf -y install java-1.8.0-openjdk maven eclipse
    sudo touch /etc/profile.d/createDevEnv.sh
    sudo sh -c "echo export JAVA_HOME=/usr/lib/jvm/java-openjdk >> /etc/profile.d/createDevEnv.sh"
    sudo sh -c "echo export PATH=$JAVA_HOME/bin:$PATH >> /etc/profile.d/createDevEnv.sh"
    sudo dnf -y update
    sudo dnf -y upgrade
    
    #sudo startx
  
   # sudo wget -O /opt/eclipse-java-luna-SR2-linux-gtk-x86_64.tar.gz http://ftp.fau.de/eclipse/technology/epp/downloads/release/luna/SR2/eclipse-java-luna-SR2-linux-gtk-x86_64.tar.gz
   # cd /opt/ && sudo tar -zxvf eclipse-java-luna-SR2-linux-gtk-x86_64.tar.gz

  SHELL
end