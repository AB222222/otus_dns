# otus_dns

Файлы прилагаю.

Вывод с client:

```
me@me-HP-260-G3-DM:~/otus-linux/DZ_DNS/vagrant-bind/provisioning$ vagrant ssh client
Last login: Sun Mar  7 10:06:21 2021 from 10.0.2.2
### Welcome to the DNS lab! ###

- Use this client to test the enviroment, with dig or nslookup.
    dig @192.168.50.10 ns01.dns.lab
    dig @192.168.50.11 -x 192.168.50.10

- nsupdate is available in the ddns.lab zone. Ex:
    nsupdate -k /etc/named.zonetransfer.key
    server 192.168.50.10
    zone ddns.lab 
    update add www.ddns.lab. 60 A 192.168.50.15
    send

- rndc is also available to manage the servers
    rndc -c ~/rndc.conf reload

Enjoy!
[vagrant@client ~]$ nslookup web1.dns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	web1.dns.lab
Address: 192.168.50.15

[vagrant@client ~]$ nslookup web1.dns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	web1.dns.lab
Address: 192.168.50.15

[vagrant@client ~]$ nslookup web2.dns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

** server can't find web2.dns.lab: NXDOMAIN

[vagrant@client ~]$ nslookup web2.dns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

** server can't find web2.dns.lab: NXDOMAIN

[vagrant@client ~]$ nslookup newdns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	newdns.lab
Address: 192.168.50.10
Name:	newdns.lab
Address: 192.168.50.11

[vagrant@client ~]$ nslookup newdns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	newdns.lab
Address: 192.168.50.11
Name:	newdns.lab
Address: 192.168.50.10

[vagrant@client ~]$ nslookup www.newdns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	www.newdns.lab
Address: 192.168.50.16
Name:	www.newdns.lab
Address: 192.168.50.15

[vagrant@client ~]$ nslookup www.newdns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	www.newdns.lab
Address: 192.168.50.16
Name:	www.newdns.lab
Address: 192.168.50.15

[vagrant@client ~]$ 
```

Теперь со второго клиента:

```
me@me-HP-260-G3-DM:~/otus-linux/DZ_DNS/vagrant-bind/provisioning$ vagrant ssh client2
Last login: Sun Mar  7 10:07:46 2021 from 10.0.2.2
### Welcome to the DNS lab! ###

- Use this client to test the enviroment, with dig or nslookup.
    dig @192.168.50.10 ns01.dns.lab
    dig @192.168.50.11 -x 192.168.50.10

- nsupdate is available in the ddns.lab zone. Ex:
    nsupdate -k /etc/named.zonetransfer.key
    server 192.168.50.10
    zone ddns.lab 
    update add www.ddns.lab. 60 A 192.168.50.15
    send

- rndc is also available to manage the servers
    rndc -c ~/rndc.conf reload

Enjoy!
[vagrant@client2 ~]$ nslookup dns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	dns.lab
Address: 192.168.50.11
Name:	dns.lab
Address: 192.168.50.10

[vagrant@client2 ~]$ nslookup dns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	dns.lab
Address: 192.168.50.10
Name:	dns.lab
Address: 192.168.50.11

[vagrant@client2 ~]$ nslookup web1.dns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	web1.dns.lab
Address: 192.168.50.15

[vagrant@client2 ~]$ nslookup web1.dns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	web1.dns.lab
Address: 192.168.50.15

[vagrant@client2 ~]$ nslookup web2.dns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

Name:	web2.dns.lab
Address: 192.168.50.16

[vagrant@client2 ~]$ nslookup web2.dns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

Name:	web2.dns.lab
Address: 192.168.50.16

[vagrant@client2 ~]$ nslookup newdns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

** server can't find newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ nslookup newdns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

** server can't find newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ nslookup www.newdns.lab 192.168.50.10
Server:		192.168.50.10
Address:	192.168.50.10#53

** server can't find www.newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ nslookup www.newdns.lab 192.168.50.11
Server:		192.168.50.11
Address:	192.168.50.11#53

** server can't find www.newdns.lab: NXDOMAIN

[vagrant@client2 ~]$ exit
logout
Connection to 127.0.0.1 closed.
me@me-HP-260-G3-DM:~/otus-linux/DZ_DNS/vagrant-bind/provisioning$ 
```

