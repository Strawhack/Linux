## Kali Linux Post Install in Virtual Box


#### Install Virtual Box Guest Addition CD Image
```sh
Copy content from Guest Addition CD Image to a folder say /tmp/image
$chmod +x VBoxLinuxAdditions.run
$sudo ./VBoxLinuxAdditions.run
```

#### Change Default Nameserver in resolv.conf
```sh
$sudo vim /etc/resolv.conf

Add the following Name Server
nameserver 8.8.8.8
nameserver 8.8.4.4
```

#### Change /etc/apt/source.list
```sh
$sudo cp /etc/apt/sources.list /etc/apt/sources.listbak

Change the mirror link
deb https://mirrors.ocf.berkeley.edu/kali/  kali-rolling main contrib non-free

Save the file and run update
$ sudo apt clean
$ sudo apt update && apt upgrade -y
```

#### Installing Nala
```sh
$sudo apt-get install nala

Commands in Nala for Update/Upgrade
$sudo nala update
$sudo nala upgrade
```

#### Installing ZSH & ZSH Plugins
```sh
Install Oh My ZSH via Curl(Installed by default in Kali 2022)
$sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

Install Oh My ZSH via Wget
$sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

Installing ZSH Auto-Suggestions
$git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

To Enable above plugin
$vim ~/.zshrc
plugins= 
(
git
zsh-autosuggestions
zsh-syntax-highlighting
)

Save the file

Installing Powerlevel10k
$git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k
echo 'source ~/.oh-my-zsh/custom/themes/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc

$source ~/.zshrc

$p10k configure

Note After installing Oh My ZSH/Powerlevel10k, many icons wont appear in Tmux, to over come this issue, make an alias in .zshrc
$vim ~/.zshrc
alias tmux='tmux -u'
```



