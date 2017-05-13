# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.hostname = "demo"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder ".", "/home/vagrant/sync", disabled: false
  config.vm.provision "shell", inline: $script
end

$script = <<SCRIPT
  yum -y install epel-release
  yum -y install nginx ansible git vim wget java-1.8.0-openjdk java-1.8.0-openjdk-devel
  wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
  rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
  yum -y install jenkins
  systemctl start jenkins.service
  git clone https://github.com/devops-book/ansible-playbook-sample.git
  systemctl start nginx
SCRIPT
