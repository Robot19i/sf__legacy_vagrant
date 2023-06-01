Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false
  config.vm.synced_folder "./repl", "/home/vagrant/"
  config.vm.host_name = "postgresql"
  config.vm.provider "virtualbox" do |vb|
  vb.memory = "512"
end
    config.vm.provision "shell", inline: <<-SHELL   
	sudo apt-get -y update
	sudo touch /etc/apt/sources.list.d/pgdg.list
    sudo echo "deb https://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
	wget --no-check-certificate -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    sudo apt-get -y update
    sudo apt-get install -y git-core curl zlib1g-dev build-essential
    sudo apt-get install -y libssl-dev libreadline-dev libyaml-dev
    sudo apt-get install -y libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev
    sudo apt-get install -y libcurl4-openssl-dev python-software-properties libffi-dev
	sudo apt-get install -y postgresql postgresql-client postgresql-contrib
    SHELL
end
