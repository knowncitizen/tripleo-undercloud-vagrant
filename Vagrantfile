Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.box_version = "1812.01"
  config.vm.network "private_network", ip: "192.168.121.166"
  config.vm.provider :virtualbox do |virtualbox|
    virtualbox.cpus = 2
    virtualbox.memory = 8192
  end
  config.vm.provision "shell", inline: <<-SHELL
    echo "export TERM=xterm">>/home/vagrant/.bashrc
    echo "export TERM=xterm">>/root/.bashrc
    yum install -y screen strace git wget net-tools vim python-setuptools python-requests
    yum install -y http://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/f/fpaste-0.3.7.4.1-2.el7.noarch.rpm
    git clone https://github.com/openstack/tripleo-repos
    cd tripleo-repos
    python setup.py install
    rm -rf /home/vagrant/tripleo-repos
    tripleo-repos current
    yum install -y python-tripleoclient
    cp /usr/share/python-tripleoclient/undercloud.conf.sample /home/vagrant/undercloud.conf
    echo "undercloud.localdomain">/etc/hostname
    hostname undercloud.localdomain
    yum update -y
    reboot
   SHELL
end
