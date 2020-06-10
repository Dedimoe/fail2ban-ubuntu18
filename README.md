# fail2ban-ubuntu18
fail2ban-ubuntu18

sudo apt-get update
sudo apt-get install fail2ban

awk '{ printf "# "; print; }' /etc/fail2ban/jail.conf | sudo tee /etc/fail2ban/jail.local

vi /etc/fail2ban/jail.conf

cari dan isi :

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

vi /etc/fail2ban/jail.local
semua yg ada enabled = true di unremark
. . .
[jail_to_enable]
enabled = true
. . .

systemctl enable fail2ban
systemctl restart fail2ban
