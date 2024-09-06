# Configuração do NSClient Windows
# Passo 1: Instalar o NSClient
NSCP-0.4.1.73-x64

# Passo 2: Deploying nsclient on windows servers
Link:https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers

# Get nsclient 32-bit and 64-bit copies from opinkerfi github repo:
cd /opt
git clone https://github.com/opinkerfi/misc

# Copy nsclient to where okconfig expects it to live:
cp -r misc/nsclient/src /usr/share/okconfig/client/windows/nsclient

# Put the ip address of the nagios server in here:
vim /usr/share/okconfig/client/windows/nsclient/datafiles/allowed_hosts.ini 

# Passo 3: Instalar o Agent no adagios
[Check Prerequisites     ] localhost.localdomain Starting..
[Check Prerequisites     ] localhost.localdomain OK
[Connection test         ] LT1475FNST Starting..
[Connection test         ] LT1475FNST OK
[Upload NSClient++ Setup ] LT1475FNST Starting..
[Upload NSClient++ Setup ] LT1475FNST OK
[Installing NSClient++   ] LT1475FNST Starting..
[Installing NSClient++   ] LT1475FNST OK

# Adagios Duvida
https://github.com/opinkerfi


# PASSOS DADOS
[root@localhost plugins]# ./check_nrpe -H 172.16.4.190
connect to address 172.16.4.190 port 5666: Connection refused
connect to host 172.16.4.190 port 5666: Connection refused
[root@localhost plugins]# ./usr/share/okconfig/client/windows//install_nsclient.sh
[root@localhost plugins]# cd /usr/share/okconfig/client/windows//
[root@localhost plugins]# cd /usr/share/okconfig/client/windows//
[root@localhost windows]# ll
total 4
-rwxr-xr-x. 1 root root 4013 Aug 26 14:38 install_nsclient.sh
[root@localhost windows]# ./install_nsclient.sh
Domain Name (DOMAIN): zap.intra
Domain user (user): afonso.caluege
Domain password:
[Check Prerequisites     ] localhost.localdomain Starting..
[Check Prerequisites     ] localhost.localdomain FATAL Directory /usr/share/okconfig/client/windows//nsclient not found\nMore info at https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers

[root@localhost windows]# cd /var/log/okconfig/
[root@localhost okconfig]# ll
total 4
-rw-r--r-- 1 root root 290 Aug 27 16:33 install_nsclient.log
[root@localhost okconfig]# chmod +x install_nsclient.log
[root@localhost okconfig]# ll
total 4
-rwxr-xr-x 1 root root 290 Aug 27 16:33 install_nsclient.log
[root@localhost okconfig]# cd /etc/naemon/adagios/
[root@localhost adagios]# ll
total 0
[root@localhost adagios]# /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg
bash: /usr/local/nagios/bin/nagios: No such file or directory
[root@localhost adagios]# ls -l /var/log/okconfig/install_nsclient.log
-rwxr-xr-x 1 root root 290 Aug 27 16:33 /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo cat /var/log/okconfig/install_nsclient.log
Tue, 27 Aug 2024 16:33:29 +0100: [Check Prerequisites     ] localhost.localdomain Starting
Tue, 27 Aug 2024 16:33:29 +0100: FATAL Directory /usr/share/okconfig/client/windows//nsclient not found
More info at https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers

[root@localhost adagios]# sudo nano /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo chmod 644 /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo chown naemon:naemon /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo cat /var/log/okconfig/install_nsclient.log
Tue, 27 Aug 2024 16:33:29 +0100: [Check Prerequisites     ] localhost.localdomain Starting
Tue, 27 Aug 2024 16:33:29 +0100: FATAL Directory /usr/share/okconfig/client/windows//nsclient not found
More info at https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers

[root@localhost adagios]# sudo nano /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo chmod 644 /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo chown yourusername:yourgroup /var/log/okconfig/install_nsclient.log
chown: invalid user: ‘yourusername:yourgroup’
[root@localhost adagios]# sudo chown naemon:naemon /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo getenforce
Disabled
[root@localhost adagios]# sudo aa-status
[root@localhost adagios]# yum remove nagios
Dependencies resolved.

Complete!
[root@localhost adagios]# systemctl restart naemon adagios httpd
[root@localhost adagios]# systemctl restart naemon adagios httpd
Warning: The unit file, source configuration file or drop-ins of httpd.service changed on disk. Run 'systemctl daemon-reload' to reload units.
[root@localhost adagios]# sudo chmod 755 /var/log/okconfig
[root@localhost adagios]#
[root@localhost adagios]# sudo chmod 664 /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo chown yourusername:yourgroup /var/log/okconfig/install_nsclient.log
chown: invalid user: ‘yourusername:yourgroup’
[root@localhost adagios]# sudo chown yourusername:yourgroup /var/log/okconfig
chown: invalid user: ‘yourusername:yourgroup’
[root@localhost adagios]# sudo chown adagios:adagios /var/log/okconfig
[root@localhost adagios]# sudo chown adagios:adagios /var/log/okconfig/install_nsclient.log
[root@localhost adagios]# sudo /usr/share/okconfig/client/windows/install_nsclient.sh
Domain Name (DOMAIN): zap.intra
Domain user (user): afonso.caluege
Domain password:
[Check Prerequisites     ] localhost.localdomain Starting..
[Check Prerequisites     ] localhost.localdomain FATAL Directory /usr/share/okconfig/client/windows//nsclient not found\nMore info at https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers
[root@localhost adagios]# cd /opt
[root@localhost opt]# git clone https://github.com/opinkerfi/misc
Cloning into 'misc'...
remote: Enumerating objects: 6705, done.
remote: Total 6705 (delta 0), reused 0 (delta 0), pack-reused 6705 (from 1)
Receiving objects: 100% (6705/6705), 169.30 MiB | 2.90 MiB/s, done.
Resolving deltas: 100% (3442/3442), done.
[root@localhost opt]# cp -r misc/nsclient/src /usr/share/okconfig/client/windows/nsclient
[root@localhost opt]# vim /usr/share/okconfig/client/windows/nsclient/datafiles/allowed_hosts.ini
[root@localhost opt]# systemctl restart naemon adagios httpd
Warning: The unit file, source configuration file or drop-ins of httpd.service changed on disk. Run 'systemctl daemon-reload' to reload units.


# Extra
https://stackoverflow.com/questions/13795027/nagios-nrpe-command-not-defined

