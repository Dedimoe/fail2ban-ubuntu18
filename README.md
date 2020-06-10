# fail2ban-ubuntu18
fail2ban-ubuntu18

install fail2ban:
```
sudo apt-get update
sudo apt-get install fail2ban
```

copy config:
```
awk '{ printf "# "; print; }' /etc/fail2ban/jail.conf | sudo tee /etc/fail2ban/jail.local
```

edit config:
```
vi /etc/fail2ban/jail.conf
```

find & replace:
```
[DEFAULT]
. . .
ignoreip = 127.0.0.1/8
. . .

[DEFAULT]
. . .
bantime = 7200
. . .

[DEFAULT]
. . .
findtime = 600
maxretry = 3
. . .

[DEFAULT]
. . .
destemail = root@localhost
sendername = Fail2Ban
mta = sendmail
. . .

[DEFAULT]
. . .
action = $(action_)s
. . .
```

edit config:
```
vi /etc/fail2ban/jail.local
```

unremark which option was: '''enabled = true```:
```
. . .
[jail_to_enable]
enabled = true
. . .
```

activate with this command:
```
systemctl enable fail2ban
systemctl restart fail2ban
```
