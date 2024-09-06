# Instalar o NSClient no Windows via SSH
[root@lt874fnst naemon]# sudo chmod -R 775 /var/log/okconfig
[root@lt874fnst naemon]# sudo chown -R $(whoami):$(whoami) /var/log/okconfig
[root@lt874fnst naemon]# sudo /usr/share/okconfig/client/windows/install_nsclient.sh
Domain Name (DOMAIN): zap.intra
Domain user (user): afonso.caluege
Domain password:
[Check Prerequisites     ] lt874fnst.zap.intra Starting..
[Check Prerequisites     ] lt874fnst.zap.intra FATAL Directory /usr/share/okconfig/client/windows//nsclient not found\nMore info at https://github.com/opinkerfi/okconfig/wiki/Deploying-nsclient-on-windows-servers

######
[root@lt874fnst naemon]# sudo mkdir -p /usr/share/okconfig/client/windows/nsclient
[root@lt874fnst naemon]# sudo chmod -R 755 /usr/share/okconfig/client/windows/nsclient
[root@lt874fnst naemon]# sudo chown -R $(whoami):$(whoami) /usr/share/okconfig/client/windows/nsclient
[root@lt874fnst naemon]# ls -ld /usr/share/okconfig/client/windows/nsclient
drwxr-xr-x 2 root root 6 Aug 19 10:09 /usr/share/okconfig/client/windows/nsclient
[root@lt874fnst naemon]# ls -ld /usr/share/okconfig/client/windows/nsclient
drwxr-xr-x 2 root root 6 Aug 19 10:09 /usr/share/okconfig/client/windows/nsclient
[root@lt874fnst naemon]# sudo /usr/share/okconfig/client/windows/install_nsclient.sh
Domain Name (DOMAIN): zap.intra
Domain user (user): afonso.caluege
Domain password:
[Check Prerequisites     ] lt874fnst.zap.intra Starting..
[Check Prerequisites     ] lt874fnst.zap.intra OK
