# HoneyResult

Tras instalar un honeypot en la red y dejandolo funcionar durante 12 horas, ha recibido 27.936 intentos de entrada.

Una vez obtenida las ip, generé el siguiente script para obtener la informacion de cada una de las ips:


		#!/bin/bash
		while read p; do
		  	curl http://ipinfo.io/$p/json?token=$2
			sleep 0.2s
		done <"$1"

Ejecute una muestra aleatoria de 1000 resultados, redirigiendo la salida del script y procesando cada uno de los json obtuvimos el siguiente mapa:

![Mapa de ataque](img/mapimage.png)

El mapa se puede visitar en este [enlace](https://drive.google.com/open?id=1x3u8aQ7zDJLjcv6KsoDhqRmmMNs&usp=sharing)

* [Tabla de  1000](tabla.md)
* [Conjunto global de ips](ip.md)