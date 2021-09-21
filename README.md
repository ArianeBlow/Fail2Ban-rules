# Fail2Ban-rules
some cool Fail2Ban rules

NginX Bot-Hunter

sudo nano /etc/fail2ban/jail.conf
```
[nginx404]
enabled = true
filter = nginx404
action   = iptables-multiport[name="nginx404", port="http,https"]
port = http, https
logpath = /var/log/nginx/access.log
findtime = 30
bantime = 500
maxretry = 10
```
sudo nano /etc/fail2ban/filter.d/nginx404.conf
```
[Definition]
failregex = ^<HOST>.*"(GET|POST).*" (404|444|403|400) .*$
ignoreregex = .*(robots.txt|favicon.ico|jpg|png|ics)
```
Restart & check
```
sudo service fail2ban restart
sudo fail2ban-client start
sudo fail2ban-client status
```
