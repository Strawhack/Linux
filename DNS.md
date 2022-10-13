# DNS

#### Nslookup

```bash
Nslookup can be used in interactive or non-interactive mode.
To start in interactive mode:
$nslookup
>

Example:
$nslookup
>www.google.com


To check for particular type[ns, A, AAAA, mx, txt, ptr, any, hinfo, soa]
$nslookup
>set type=ns
>google.com

-------------------------------------------------------------------------
View Domain's NS Records
nslookup -type=ns google.com

View Domains MX Records
nslookup -type=mx google.com

Perform a Reverse DNS Lookup
nslookup [ip-address]

View SOA Records
nslookup -type=soa [domain-name]

View Text Records
[TXT records contain important information for users 
outside of the domain.]
nslookup -type=txt [domain-name]

View All Records
nslookup -type=any [domain-name]

View Information About a Specific Name Server
nslookup [domain-name] [name-server]

View Pointer Records
nslookup -type=ptr [reverse-ip-address].in-addr.arpa

Query a Non-Default Port
nslookup -port=[port-number] [domain-name]

View Debugging Information
nslookup -debug [domain-name]
```

#### Dig

```bash
$dig [server] [name] [type]

------------------------------------------------------------------------
To query domain “A” record
$dig google.com
$dig A google.com @DNS_IP
$dig AAAA google.com @DNS_IP

To query domain “A” record with +short
$dig google.com +short

To remove comment lines
$dig google.com +nocomments


To set or clear all display flags
$dig google.com +noall

To query detailed answer
$dig google.com +noall +answer

To query all DNS record types
$dig google.com ANY
$dig any victim.com @dns_ipaddress

To query MX/TXT record
$dig google.com MX
$dig MX @DNS_IP google.com 
$dig TXT @DNS_IP google.com
$dig NS @DNS_IP google.com

To trace DNS path
$dig google.com +trace

To specify name server
$dig google.com @8.8.8.8

To perform Reverse DNS Lookup
$dig +noall +answer -x 8.8.8.8
$dig -x ip_address @DNS_IP
$dig -x ipv6_address @DNS_IP

Zone Transfer
$dig axfr @dns_ip #Try zone transfer without domain
$dig axfr @<DNS_IP> <DOMAIN> #Try zone transfer guessing the domain
$fierce --domain <DOMAIN> --dns-servers <DNS_IP>
```

#### Nmap For DNS

```bash
#Perform enumeration actions
$nmap -n --script "(default and *dns*) or fcrdns or dns-srv-enum or dns-random-txid or dns-random-srcport" <IP>
```

#### DNS Subdomain

```bash
$dnsenum --dnsserver <IP_DNS> --enum -p 0 -s 0 -o subdomains.txt -f subdomains-1000.txt <DOMAIN>
$dnsrecon -D subdomains-1000.txt -d <DOMAIN> -n <IP_DNS>
$dnscan -d <domain> -r -w subdomains-1000.txt #Bruteforce subdomains in recursive way, https://github.com/rbsec/dnscan
```

## Useful Links

> Program Used for DNS Tunneling 
> 
> https://github.com/yarrick/iodine
> 
> Out of Band Data exfiltration
> 
> https://www.youtube.com/watch?v=p8wbebEgtDk
> 
> Hacktricks
> 
> https://book.hacktricks.xyz/network-services-pentesting/pentesting-dns
