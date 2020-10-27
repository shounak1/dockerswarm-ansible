Vagrant.configure("2") do |config|
  servers = [
  	{
  		:hostname => "ansible-control",
  		:box => "hashicorp/bionic64",
  		:ip => "192.168.56.200",
  		:ssh_port => "2215",
  		:memory => "512"
  	},
  	{
  		:hostname => "swarm-node-1",
  		:box => "hashicorp/bionic64",
  		:ip => "192.168.56.201",
  		:ssh_port => "2210",
  		:memory => "512"
  	},
  	{
  		:hostname => "swarm-node-2",
  		:box => "hashicorp/bionic64",
  		:ip => "192.168.56.202",
  		:ssh_port => "2211",
  		:memory => "512"
  	}
  ]

  servers.each do |machine| 
  	config.vm.define machine[:hostname] do |node|
  		node.vm.box = machine[:box]
  		node.vm.hostname = machine[:hostname]
  		node.vm.network "private_network", ip: machine[:ip]
  		#node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"

  		node.vm.provider "virtualbox" do |v|
  			v.customize ["modifyvm", :id, "--memory", machine[:memory]]
  			v.customize ["modifyvm", :id, "--name", machine[:hostname]]
  		end
  	end
  end
end