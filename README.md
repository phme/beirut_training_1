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
