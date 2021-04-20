# My ubuntu 20 Setup

## Create a new user
```bash
adduser --disabled-password <your_username>
usermod -aG sudo <your_username>
su - <your_username>
```
And then update `.ssh/authorized_keys` with your ssh public key.

## Install zsh
```bash
sudo apt install -y zsh
sh -c "$(curl -fsSL https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh)"
```

## Setup my system
```bash
chmod +x ./setup.sh ./tmux.sh
./setup.sh
```
Follow the prompt and finish installing all softwares.
```bash
source ~/.zshrc
```

## Optional
Open .zshrc and replace the theme with powerlevel10k

## 临时代理
```bash
export http_proxy=http://192.168.6.101:53952
export https_proxy=https://192.168.6.101:53952
```

## .gitconfig  git http代理
```bash
git config --global http.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
```

```
[http "https://githubusercontent.com"]    
  proxy = https://192.168.100.7:2471    
[http]
  proxy = http://192.168.100.7:2471
```

## git ssh代理
touch /.ssh.config

```
Host github.com
    User git
    ProxyCommand nc -X connect -x 192.168.100.101:53952 %h %p
	
	
#Amazon EC2
Host *.compute.amazonaws.com
    ProxyCommand nc -X connect -x 192.168.100.101:53952 %h %p
```

## vscode
```
Toggle Terminal 进入命令行
mkdir Projects
code Projects 使用vs code打开Projects
```


