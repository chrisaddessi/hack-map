# Path A
###### non-cloud hosted sites

# Step A1
## Port Scanning
Take note of the services and their versions found.

### Nmap
```
proxychains nmap -sT -PN -n -sV -p* 8.8.8.8 -oN nmap-initial.txt
nmap -Pn -s
sudo nmap -e tun0 8.8.8.8 -sV -sC -sS -A -v -p* -oN nmap_2.txt
nmap -sS -T2 8.8.8.8
sudo nmap -sTU -O 8.8.8.8
```

### Rustscan
very intensive
```
```
### masscann
```
```

### Nmap Scripts
```bash
ls /usr/share/nmap/scripts/
```
```bash
ls -la /usr/share/nmap/scripts | grep "heartbleed"
ssl-heartbleed.nse
sudo nmap -sS -sV -F -p 443 8.8.8.8 --script=ssl-heartbleed -oN nmap-scan.txt
```


## Next Steps
[link to standard](https://github.com/chrisaddessi/hack-map/tree/main/attack-for-root/standard)
