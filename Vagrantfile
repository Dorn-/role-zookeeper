# -*- mode: ruby -*-
#
# Vagrantfile for role tests
#

# ROLE_NAME: name of role to test
# BOX_IMAGE: image for box
# BOX_MEMORY: how much memory do we need
# BOX_NAME: image name

ROLE_NAME  = "role-zookeeper"
BOX_IMAGE  = "http://udp-proxy.fiducial.dom/centos/centos73.json"
BOX_NAME   = "CentOS/7.3"
BOX_MEMORY = 512

####
$key_search=%w/github_rsa id_rsa id_dsa/

$script = <<SCRIPT
ssh-keyscan github.fiducial.dom >> ~/.ssh/known_hosts
yum install -y git
cd
if [[ -d ansible-utils ]]; then
  (cd ansible-utils; git checkout .; git pull)
else
  git clone git@github.fiducial.dom:SIINFRA/ansible-utils.git
fi
cd ansible-utils && test/role-specs.sh --install #{ROLE_NAME}
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "#{BOX_NAME}"
  config.vm.hostname = "#{ROLE_NAME}"

  private_key = $key_search.select{ |x| File.exists?(File.join(Dir.home, ".ssh", x)) }.first
  private_key = File.join(Dir.home, ".ssh", private_key)
  private_key = File.read(private_key) rescue nil
  config.vm.network :forwarded_port, guest: 8983, host: 8983

  # Forward nécessaire pour que les dépendances (requirements.yml) puissent
  # être tirées
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |v|
    v.name   = "#{ROLE_NAME}"
    v.memory = "#{BOX_MEMORY}"
    v.linked_clone = true
  end

  config.vm.provision(:shell, :inline => "mkdir -p /root/.ssh && echo '#{private_key}' > /root/.ssh/id_rsa && chmod 400 /root/.ssh/id_rsa")
  config.vm.provision(:shell, :inline => "echo '#{private_key}' > /home/vagrant/.ssh/id_rsa && chmod 400 /home/vagrant/.ssh/id_rsa && chown vagrant:vagrant /home/vagrant/.ssh/id_rsa")
  config.vm.provision "shell", :inline => $script
end
