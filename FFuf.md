### FFUF

```
Directory Fuzzing

$ffuf -w path_to_wordlist:FUZZ -u http://ip_address:port/FUZZ -ic -t 200 -v
Where:
-u   URL 
-w   Wordlist to be used for fuzzing
-ic  Ignore wordlist comments
-t   Number of concurrent threads. (default: 40)
-v   Verbose output, printing full URL and redirect location
```


```
Extension Fuzzing

$ffuf -w path_to_wordlist:FUZZ -u http://ip_address:port/indexFUZZ

For Web extenion "Seclist/Discovery/Web-Content/web-extension"

$ffuf -u http://ip_address:port/FUZZ -w path_to_wordlist -e .bak,.php,.txt,.aspx
Where
-e  For Specific extention
```

```
With Multiple Location

ffuf -u https://FUZZDOMAIN/FUZZDIR -w ./domains.txt:FUZZDOMAIN,./wordlist.txt:FUZZDIR 
or
$ffuf -u https://W2/W1  -w ./wordlist.txt:W1,./domains.txt:W2
(This would scan each of the domains in our domains.txt files using
the wordlist from wordlist.txt)
This would scan each of the domains in our domains.txt files using
the wordlist from wordlist.txt
```

```
Page Fuzzing

$ffuf -w path_to_wordlist:FUZZ -u http://ip_address:port/blog/FUZZ.php

.php will be added to wordlist while fuzzing
```

```
Recursive Fuzzing

Flag Used
-recursion        Scan recursively. Only FUZZ keyword is supported, 
                  and URL (-u) has to end in it
-recursion-depth  Maximum recursion depth. (default: 0)

$ffuf -w path_to_wordlist:FUZZ -u http://ip_address:port/FUZZ -recursion \
 -recursion-depth 1 -e .php -v
 ```
 
 ```
 Sub-Domain Fuzzing
 
 Wordlist : /opt/SecLists/Discovery/DNS/
 
 $ffuf -w path_to_wordlist:FUZZ -u https://FUZZ.web_address:port/
 
 VHOST Discover
 $ffuf -w path_to_wordlist.txt:FUZZ -u https://website.com/ \
 -H "HOST: FUZZ.website.com"
 
 
 Using Gobuster
 $gobuster dns -d domain.com -w wordlist
 ```
 
 
 ```
 VHOST Fuzzing
 
When it came to fuzzing sub-domains that do not have a public DNS record 
or sub-domains under websites that are not public, then we use VHOST.
VHosts may or may not have public DNS records.

$ffuf -w path_to_wordlist:FUZZ -u http://academy.com:PORT/ -H \
'Host: FUZZ.academy.htb'
```

```
Filtering Options

MATCHER OPTIONS:
  -mc  Match HTTP status codes, or "all" for everything.
       (default:200,204,301,302,307,401,403)
  -ml  Match amount of lines in response
  -mr  Match regexp
  -ms  Match HTTP response size
  -mw  Match amount of words in response

FILTER OPTIONS:
  -fc  Filter HTTP status codes from response. Comma separated list of codes 
  -fl  Filter by amount of lines in response. 
       Comma separated list of line counts and ranges
  -fr  Filter regexp
  -fs  Filter HTTP response size. Comma separated list of sizes and ranges
  -fw  Filter by amount of words in response. 
       Comma separated list of word counts and ranges
```


```
Parameter Fuzzing - GET

We will use ffuf to enumerate parameters. Let us first start with fuzzing
for GET requests, which are usually passed right after the URL, with a ? symbol

Example:
http://admin.academy.htb:PORT/admin/admin.php?param1=key

WordList:
/opt/SecLists/Discovery/Web-Content/burp-parameter-names.txt

$ffuf -w path_to_wordlist:FUZZ -u \
-u http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key -fs xxx
```


```
Parameter Fuzzing - POST

The main difference between POST requests and GET requests is that POST 
requests are not passed with the URL and cannot simply be appended 
after a ? symbol. POST requests are passed in the data field within 
the HTTP request

To fuzz the data field with ffuf, we can use the -d flag, 
as we saw previously in the output of ffuf -h. 
We also have to add -X POST to send POST requests.

$ffuf -w path_to_wordlist:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php \
-X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded'

Assume we got 'id', to verify
$curl http://admin.academy.htb:PORT/admin/admin.php -X POST \
-d 'id=key' -H 'Content-Type: application/x-www-form-urlencoded'


Value Fuzzing
After finding the parameter, we now have to fuzz the correct value that would 
return the correct value of the flag. 

$ffuf -w path_to_wordlist:FUZZ -u http://admin.academy.htb:PORT/ \
admin/admin.php -X POST -d 'id=FUZZ' \
-H 'Content-Type: application/x-www-form-urlencoded'
```


### Brute Force Login
```
$ffuf -w /path_to_file/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.150.57/customers/signup -mr "username already exists"

Create a Valid_Username list, now lets brute force Password
$ffuf -w valid_usernames.txt:W1,/path_to_password_list:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.150.57/customers/login -fc 200
```

