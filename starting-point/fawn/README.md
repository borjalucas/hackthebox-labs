# Fawn - Hack The Box

## Introducción
Máquina de nivel "Starting Point" enfocada en la enumeración del servicio FTP(File Transfer Protocol) y el aprovechamiento de configuraciones de acceso anónimo.

## Enumeracion:
**Ping**: `ping {TARGET_IP}` para verificar conexión.
**Nmap**:`nmap -sV {TARGET_IP}`
   - Resultado: Identificamos el **puerto 21/tcp** abierto corriendo el servicio **FTP**, tambien se identifica la version actual del servicio corriendo en ese puerto **vsftpd 3.0.3**.

## Explotacion:
**$ftp {TARGET_IP}:** nos conectamos al host de destino con este comando.
**Hallazgo:** El servicio FTP permite el login "Anonymous".
**Login:**
   - Name: `anonymous`
   - Password: (vacío / presionar Enter)
**Comandos dentro de FTP:**
   - `ls` para ver archivos.
   - `get flag.txt` para descargar la bandera a mi máquina.

**Obtener la bandera:**
  - `ls` en la shell del programa para ver si descargamos correctamente el archivo flag.txt
  - `cat flag.txt` para capturar definitivamente la bandera. 

**Lo aprendido:** Aprendí que el protocolo FTP es para transferencia de archivos y que el acceso anónimo es una vulnerabilidad crítica si contiene datos sensibles.
