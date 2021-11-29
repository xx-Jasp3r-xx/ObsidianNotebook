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
db_nmap -A --script vulners -v -oA Empire 10.10.159.89
```

now that we have data inside our database we can check the open ports and services on the host. as well as vulnerabilities
```bash
services
hosts
vulns
```

if no vulns show up then we can run an exploit suggester
```bash