$ docker pull tykoh/mysql:5.7-zmara

$ docker run --name mysql-zmara -e MYSQL_ROOT_PASSWORD=myrootpassword -d tykoh/mysql:5.7-zmara


Using a custom MySQL configuration file
$ docker run --name mysql-zmara \
-v /Users/tykoh/mysql/mysql-conf.d:/etc/mysql/conf.d \
-v /Users/tykoh/backup:/host \
-e MYSQL_ROOT_PASSWORD=myrootpassword \
-d tykoh/mysql:5.7-zmara


# Zmara
=======
backup full:
$ mysql-zrm-scheduler --now --backup-set dailyrun --backup-level 0

backup incremental:
$ mysql-zrm-scheduler --now --backup-set dailyrun --backup-level 1


restore:
$ mysql-zrm --action restore --backup-set dailyrun \
  --source-directory /var/lib/mysql-zrm/dailyrun/20151017093958
