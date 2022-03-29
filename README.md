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

curl https://deb.nodesource.com/setup_16.x | sudo -E bash
sudo apt-get install -y nodejs
