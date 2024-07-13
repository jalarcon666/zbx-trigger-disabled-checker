# zbx-trigger-disable-checker
Controlador de triggers deshabilitados en Zabbix.

Añadir a crontab: mysql zabbix -t -e "SELECT DISTINCT host AS Host, g.name AS Host_Group, t.description AS Disabled_Trigger, f.triggerid AS Trigger_ID FROM triggers t INNER JOIN functions f ON ( f.triggerid = t.triggerid ) INNER JOIN items i ON ( i.itemid = f.itemid ) INNER JOIN hosts h ON ( i.hostid = h.hostid ) INNER JOIN events e ON ( e.objectid = t.triggerid ) INNER JOIN hosts_groups hg ON ( hg.hostid = h.hostid ) INNER JOIN hstgrp g ON ( g.groupid = hg.groupid ) WHERE t.status =1;" > /var/log/zabbix/zabbix_disabled_triggers.log

Crear fichero zabbix_disabled_triggers.conf en /etc/zabbix/zabbix_agentd.d con UserParameter=zabbix-disabled-triggers.XXXX,cat /var/log/zabbix/zabbix_disabled_triggers.log

Añadir ITEM a Zabbix:

![image](https://github.com/user-attachments/assets/fad40daa-28d8-4fc7-bec3-2bf3d831dc12)

Añadir WIDGET al Dashboard:

![image](https://github.com/user-attachments/assets/46571420-04d2-464d-a691-d6ce7c7e9adf)
