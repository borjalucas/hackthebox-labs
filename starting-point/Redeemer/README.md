# Redeemer - Hack The Box

## Introducción
Máquina de Starting Point enfocada en la enumeración de bases de datos NoSQL, específicamente **Redis**.

### Análisis del Servicio: Redis
En esta máquina exploramos **Redis**, un motor de base de datos NoSQL que funciona como un diccionario de **key-value**. 

* **Uso común:** Se emplea como caché para datos que necesitan ser leídos a gran velocidad.
* **Vulnerabilidad detectada:** Al ser un servicio diseñado para la velocidad en redes internas, a menudo se configura sin contraseña. En esta máquina, pudimos acceder a los datos persistentes en disco simplemente conectándonos al puerto **6379**.

## Enumeración
1. **Nmap:** `nmap -p- --min-rate 5000 {TARGET_IP}`
   - Resultado: Puerto **6379/tcp** abierto.
   - Servicio: **Redis**.
  
## Explotación
1. **Conexión:** Usé `redis-cli` para conectar directamente al host sin contraseña.
   - Comando: `redis-cli -h {TARGET_IP}`

2. **Navegación interna:**
   - `info`: Para ver información del servidor y confirmar que había una base de datos con llaves (keys).
   - `select 0`: Para seleccionar la base de datos por defecto.
   - `keys *`: Para listar todas las llaves almacenadas.
   - `get flag`: Comando final para obtener el valor de la bandera.
  
## Conceptos Aprendidos
* **Redis (Remote Dictionary Server):** Es un almacén de datos en memoria rápido.
* **Mala configuración:** El servidor permitía conexiones remotas sin requerir autenticación (contraseña), exponiendo toda la base de datos.
