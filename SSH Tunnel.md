```bash
ssh -p 2222 tunneler@164.90.144.180 tunneler
```
username and password is tunneler

this is for the first challenge
```bash
ssh -fNT -L 0.0.0.0:8080:10.174.12.14:80 tunneler@164.90.144.180 -p 2222
```

navigate to localhost(127.0.0.1) if you get no errors

this is for the second challenge
```bash
ssh -fNT -L 0.0.0.0:8022:10.218.176.199:22 tunneler@164.90.144.180 -p 2222
```

this checks your open ports or if we have a tunnel
```bash
netstat -tulvp
```

now we connect to localhost using the credentials given
password is cocktailparty
```bash
ssh whistler@127.0.0.1 -p 8022
```

now we get new challenges but this is a reverse ssh ((ssh <from><to> <through>))

```bash
ssh -fNT -R 10.112.3.199:58680:127.0.0.1:8060  whistler@127.0.0.1 -p 8022
```

pivot 2 challenge
```bash
ssh -fNT -L 0.0.0.0:8082:10.112.3.12:22 whistler@127.0.0.1 -p 8022
ssh crease@127.0.0.1 -p 8023
```