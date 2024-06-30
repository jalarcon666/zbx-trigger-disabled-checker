# zbx-trigger-disable-checker
Controlador de triggers deshabilitados en Zabbix.


Idea:

Script en bash que lanza la consulta contra la base de datos de Zabbix, guarda los datos del Host y el trigger deshabilitado en memoria y los concatena con los datos del Audit LOG donde se vea la fecha y hora en la cual el trigger se deshabilitó

Con estos datos volcados en un LOG podemos crear en zabbix un item que lea este LOG cada X dias, si hay datos le metemos ACK, pero lo importante es que desde la interfaz de Zabbix podemos ver de un vistazo los triggers deshabilitados.

Lo ideal sería que esta alerta se recupere teniendo algun fichero de exclusiones donde se añadan los Host a mano para evitar que lleguen a entrar en este LOG y por consiguiente disparen la alerta.
