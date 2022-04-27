# Enumeration & Recon

### Website Tools
OWASP ZAP <br />
Burp Suite
### Directory Brute forcing
###### directory, directories, url, uri
Thes tools enumerate directories in the url
### wfuzz
### gobuster
```bash
gobuster dir -u http://8.8.8.8 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -o gobuster.txt
```
### dirb
directory buster terminal version looks for directory extensions
```bash
dirb https://wordpress.org -w /usr/share/wordlists/dirb/common.txt -o dirbscan.txt
```

### dirbuster
```
put in ip http://8.8.8.8:80/
```

### feroxbuster
```bash
feroxbuster --url http://8.8.8.8/ --wordlist /SecList/Discovery/web-content/raft-small-files-lowercase.txt
```
## Look at Web Requests
###### screenshots
###
```bash
cutycapt --url=http://api-prod.horizontall.htb/admin/init --out=test.png
```

```python
#python3 view-ferox-scan-screenshots.py api-prod.horizontall.htb.ferox-scan.txt
import argparse
import threading
import subprocess
import os 

out = subprocess.Popen(['which', 'cutycapt'], stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
stdout,stderr = out.communicate()
print(stdout)
if "not found" in str(stdout):
	print("You are missing cutycapt which is required.")
	quit()

parser = argparse.ArgumentParser()
parser.add_argument("file", help="feroxbuster scan .txt file")
args = parser.parse_args()

response_code = str(200)
extension = ".png"

lines = []

with open(args.file, "r") as sf:
	for line in sf:
		linec = line.split(" ")
		if response_code in linec[0]:
			line = line.replace("\n", "")
			line = line.split(" ")
			line = line[len(line) -1 ]
			print(str(line))
			lines.append(str(line))
def get_web_page(url):
	print(str(url))
	justurl = url.split("//")
	safeurl = justurl[1].replace("/", "%2")
	command = "cutycapt --url=" + str(url) + " --out=" + str(args.file) + "-dir/" + str(safeurl) + extension 
	#print(command)
	os.system(command)
def run_item(f, url):
    result_info = [threading.Event(), None]
    def runit():
        result_info[1] = f(url)
        result_info[0].set()
    threading.Thread(target=runit).start()
    #return result_info

os.system("mkdir " + str(args.file) + "-dir")
result_infos = [run_item(get_web_page, item) for item in lines]
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
### nikto
```bash
nikto -h zonetransfer.me
```
### cmsmap
https://github.com/Dionach/CMSmap
### wordpresscan
https://github.com/wpscanteam/wpscan


### Other Services that might be seen



