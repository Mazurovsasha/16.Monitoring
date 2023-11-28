## Установка Zabbix

1. Создаем БД для zabbix (в данном случаи mysql)

```bash
 ansible-playbook -i inv.yaml mysql.yaml -e name_db=zabbix -e user_db=zabbix -e pass_db=zabbix -u root
```

либо 

```bash
CREATE DATABASE zabbix;
CREATE USER 'zabbix' IDENTIFIED BY 'zabbix';
GRANT ALL ON zabbix.* TO 'zabbix' WITH GRANT OPTION;
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'zabbix';
```

2. Создаем новый namespace для служб мониторинга

```bash
kubectl create namespace monitoring
```

Github repo [https://github.com/Mazurovsasha/16.Monitoring/tree/master/zabbix]