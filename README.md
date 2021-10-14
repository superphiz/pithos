# pithos

#https://github.com/parithosh/consensus-deployment-ansible.git

sudo apt update && sudo apt dist-upgrade -y

sudo groupadd docker

sudo usermod -aG docker `id -un -- 1000`

sudo reboot

sudo apt install git

# install docker
# https://docs.docker.com/engine/install/ubuntu/

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

#install docker-compose
#https://docs.docker.com/compose/install/

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose


sudo chmod +x /usr/local/bin/docker-compose


# clone the repo

git clone https://github.com/parithosh/consensus-deployment-ansible.git

cd consensus-deployment-ansible/scripts/quick-run/

mkdir -p execution_data beacon_data

nano pithos.vars (insert your ip)


5. Start the execution client:

`docker-compose --env-file pithos.vars -f docker-compose.geth.yml up -d`

6. Start the consensus client:

`docker-compose --env-file pithos.vars -f docker-compose.lighthouse.yml up -d`
