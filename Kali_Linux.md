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



