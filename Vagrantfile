Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.hostname = "ubuntu"

  config.vm.provision "file", source: "./data", destination: "$HOME/remote/data"

  config.vm.provision "shell", inline: <<-SHELL
    echo "-------------------- Updating package lists"
    sudo apt-get update

    echo "-------------------- Installing supporting software"
    sudo apt-get install software-properties-common

    echo "-------------------- Adding Deadsnakes PPA"
    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt-get update

    echo "-------------------- Installing required packages"
    sudo apt-get install -y python3.10 python3-pip libpq-dev

    echo "-------------------- Installing Python libraries"
    sudo pip3 install psycopg2-binary Django
  SHELL
end
