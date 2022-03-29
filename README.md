# Beirut Training day 1
Day 1 of Beirut training (March 2022)

```bash

cd ~
curl -sfL https://direnv.net/install.sh | bash
echo 'eval "$(direnv hook bash)"' >> ~/.bashrc

curl -L https://pyenv.run | bash
echo 'export PATH="~/.pyenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc

source ~/.bashrc
sudo apt install openssl zlib1g libedit-dev
# install python 3.9.10 in pyenv
pyenv install 3.9.10

curl https://deb.nodesource.com/setup_16.x | sudo -E bash –
sudo apt-get install -y nodejs

```

## Create gitlab account and ssh key pair
```bash
# Generate an SSH key pair
ssh-keygen -t rsa -b 2048 -C "your@email.address"

# Configure your ssh config for Gitlab
cd ~/.ssh
code .

# GitLab.com
Host gitlab.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa

# Add your ssh key to your Gitlab account

# Verify you can connect
ssh -T git@gitlab.example.com

# Clone the training repository
git clone git@gitlab.com:MasaeAnalytics/common/yemen_emis/yemen_emis_training_beirut.git
# Open it in VS Code
cd yemen_emis_training_beirut
code .
```

## Postgres
```bash
# update packages list and install
sudo apt update && sudo apt upgrade –y
echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
sudo apt install postgis postgresql-13-postgis-3

# make sure your local user can log in 
cd /etc/postgresql/13/main/
sudo code pg_hba.conf

# Change peer to trust for local host
local     all	all	trust
host      all       all     127.0.0.1/32    trust
host      all       all     ::1/128         trust

# start service
sudo service postgresql start

# connect to the postgres database with user postgres
sudo su – postgres
psql –d postgres

# add local user
postgres=# create role xxxxx with superuser createdb createrole login encrypted password ‘xxxxxxx’;
postgres=# \q
exit
