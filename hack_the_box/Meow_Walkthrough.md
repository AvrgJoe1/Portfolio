# Hack The Box "Meow" Walk-Through



## Connect to VPN
    openvpn (path_to.ovpn)

    Target IP 10.129.91.72

## Recon
#### Run a nmap scan
    nmap -sC -sV -oN nmapscan 10.129.91.72
![alt text](image-1.png)

### Open Ports
    Found that port 23/tcp telnet is open

![alt text](image-2.png)


### Connected to telnet

    telnet 10.129.91.72
![alt text](image-3.png)


## Privilege Escalation
    Login using root


### Search files
    ls
![alt text](image-4.png)

### Read the file 
![alt text](image-5.png)

## Remediation 