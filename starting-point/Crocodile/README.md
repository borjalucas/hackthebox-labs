# Crocodile — Hack The Box
# Servicios:
-FTP (file transfer protocol) vsftpd 3.0.3

-Apache httpd 2.4.41

##  Enumeracion
-Puertos abiertos encontrados: FTP (21), HTTP (80)

-Accedemos a FTP mediante este comando: FTP {TARGET_IP}

-Anonymous FTP login permitida

-Encontre credenciales del admin dentro de los archivos del ftp

## Acceso a la web:
-Use las credenciales descubiertas para entrar como usuario a la web

## Información clave
La información confidencial almacenada en directorios FTP de acceso público puede provocar la exposición de credenciales.

## Que aprendi?
-Siempre revisar si el servvicio FTP te deja acceder como anonimo

-Buscar credenciales en archivos expuestos
