**history**

muestra las últimas órdenes introducidas en el Shell.

Algunos comandos relacionados con el Command history son:

* 
	```!!``` Repite la última orden
* ```!n``` Repite la orden n-Žesima
* ```!string``` Repite la orden más reciente que empiece por la cadena string
* ```!?string``` Repite la orden más reciente que contenga la cadena string
* ```\^str1\^str2``` OR ```!!:s/str1/str2/``` (substitute) Repite la última orden reemplanzando
la primera ocurrencia de la cadena str1 por la cadena str2
* ```!!:gs/str1/str2/``` (global substitute) Repite la última orden reemplazando todas las
ocurrencias de la cadena str1 por la cadena str2
* ```!$``` Es el último argumento de la orden anterior que se haya tecleado.
