cd /etc/

```
-rw-r--r-- 1 root root 1352 Jan 12  2022 default.conf
-rw-r--r-- 1 root root  629 Jan 12  2022 eparinay.conf-bk
-rw-r--r-- 1 root root 1236 May  2 07:42 m.eparinay.com.conf
-rw-r--r-- 1 root root  750 Jan 12  2022 phpmyadmin.conf
-rw-r--r-- 1 root root 1356 Jan 12  2022 purabtech.conf
-rw-r--r-- 1 root root 1224 May  2 07:07 qa.eparinay.com.conf
[purab@vps147238 conf.d]$ pwd
/etc/nginx/conf.d
[purab@vps147238 conf.d]$
```

crontab -e
```
0 0 */10 * * certbot renew >> /logs/certbot-cron.log 2>&1
```

check mariadb running or not? if stopped then start

*/30 * * * * /bin/sh /home/purab/mdb.sh
```
[root@vps147238 conf.d]# cat /home/purab/mdb.sh
service=mariadb
if (( $(ps -ef | grep -v grep | grep $service | wc -l) > 0 ))
then
echo "$service is running!!!"
else
 systemctl start mariadb.service
fi
```

more info -https://purabtech.in/how-to-install-certbot-ssl-certificate-on-nginx-server/
