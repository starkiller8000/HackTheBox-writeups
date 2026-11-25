
<img width="645" height="262" alt="image" src="https://github.com/user-attachments/assets/ad22174c-e2c0-47d1-8d34-f2105b1cd4a3" />

curl -s http://10.129.2.37:80 | html2text | grep -i 'inlanefreight'

=> info@inlanefreight.local Contact Support

gobuster vhost -u http://inlanefreight.local:80 -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt --append-domain

=> blog.inlanefreight.local:80 Status: 301 [Size: 0] [--> http://blog.inlanefreight.local/]
