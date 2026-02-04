# Meow - Hack The Box

## introduccion:
Starting Point machine focused on basic service enumeration and Telnet misconfiguration.

## Enumeracion: Es el proceso de mapear y analizar una máquina objetivo para entender cómo está configurada y qué servicios ofrece.

-ping {TARGET_IP}  se usa para comprobar la conectividad entre tu maquina (atacante) y la maquina objetivo dentro del VPN.

-nmap -sV {TARGET_IP} se usa para escanear todos los puertos abiertos de la maquina objetivo y determinar los servicios que corren en el.

-identificamos el port 23/tcp en un estado abierto corriendo con el servicio de telnet.

## Explotación
1. Conexión mediante Telnet: `telnet {TARGET_IP}`
2. Login: Se utilizó el usuario `root` sin contraseña para obtener acceso total.
3. Flag: Se localizó usando ls en la shell en `/root/flag.txt`.
