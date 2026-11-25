
<img width="645" height="262" alt="image" src="https://github.com/user-attachments/assets/ad22174c-e2c0-47d1-8d34-f2105b1cd4a3" />

curl -s http://10.129.2.37:80 | html2text | grep -i 'inlanefreight'

=> info@inlanefreight.local Contact Support

gobuster vhost -u http://inlanefreight.local:80 -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt --append-domain

=> blog.inlanefreight.local:80 Status: 301 [Size: 0] [--> http://blog.inlanefreight.local/]

1) Identify the WordPress version number.

wpscan --url http://blog.inlanefreight.local:80 --enumerate --api-token lt4NL8W6nT758d3wfOuhq...

2) Identify the WordPress theme in use.
curl -s -X GET http://blog.inlanefreight.local:80 | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2

=> twentynineteen
