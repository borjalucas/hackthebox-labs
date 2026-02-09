# Dancing - Hack The Box

## Introducción:
Máquina de Starting Point enfocada en la enumeración de servicios de archivos compartidos en Windows mediante el protocolo SMB(Server Message Block).

Hay multiples formas de transferir un archivo mediante 2 hosts en la misma red, Usando el protocolo SMB, una aplicación (o el usuario de una aplicación) puede acceder a archivos en un servidor remoto, junto con otros recursos como impresoras.

## Enumeracion: 
**Nmap:** `nmap -sV {TARGET_IP}`
   - Resultado: Puerto **445/tcp** abierto (microsoft-ds).

**SMB Enumeración:** Usé `smbclient -L {TARGET_IP} -N` para listar los recursos compartidos sin contraseña.
   - Recursos encontrados: `ADMIN$`, `C$`, `IPC$`, `WorkShares`
   - smbclient es el programa de terminal que usas para navegar y descargar archivos de servidores Windows que comparten carpetas en la red

## Explotacion:
**Acceso:** conexion a la carpeta compartida que nos permitio el sistema: `smbclient \\\\{TARGET_IP}\\WorkShares`

**Navegacion:** 
  - Entre en la carpeta de James.p usando `cd`
  - `ls` en la carpeta de James.P
  - `get flag.txt` el comando utilizado para obtener la bandera



## Conceptos Teóricos Aprendidos

### ¿Por qué esta máquina es vulnerable?
El protocolo **SMB (Server Message Block)** está diseñado para compartir archivos mediante autenticación (usuario/password). Sin embargo, en esta máquina explotamos una **mala configuración del administrador**.

En lugar de proteger el recurso compartido (share), el administrador permitió:
* **Anonymous Log-ons:** El servidor no verifica quién intenta entrar.
* **Falta de privilegios mínimos:** Una carpeta con archivos sensibles (WorkShares) era accesible para cualquier usuario no autenticado.
*  El puerto **445** es clave para SMB en Windows.
