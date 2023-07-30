# EscanerDeRedConPython

## Mi proyecto Explicado (Librerías y sus funciones)
### La librería `import socket` 
Este módulo proporciona operaciones de socket y algunas funciones relacionadas.
1. `s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)` → Las constantes `AF_*` y `SOCK_*` son colecciones `AddressFamily` y `SocketKind IntEnum` respectivamente. 
- `socket.AF_INET`: Estas constantes representan las familias de direcciones (y protocolos), utilizadas para el primer argumento de `socket()`
- `socket.SOCK_DGRAM`: Estas constantes representan los tipos de socket, usados para el segundo argumento de socket(). Es posible que haya más constantes disponibles según el sistema. (Solo SOCK_STREAM y SOCK_DGRAM parecen ser útiles en general).
2. `s.connect(("8.8.8.8", 80))`: Se hace una conexión al DNS (8.8.8.8) de Google. (host = El host remoto, port =  El mismo puerto que utiliza el servidor)
3. `host_ip = s.getsockname()[0]`: Se revisa la dirección usada como fuente de la comunicación. Retorna una dirección. El método `getsockname` → Devuelve la propia dirección del socket. Esto es útil para averiguar el número de puerto de un socket IPv4/v6, por ejemplo. (El formato de la dirección devuelta depende de la familia de direcciones). Devuelve una array: 
- `[0]` → Es la IP
- `[1]` → Es el puerto
5. `s.close()`: Libera el recurso asociado con una conexión, pero no necesariamente cierra la conexión de inmediato.
Nota: Esto supone que tiene acceso a Internet y que no hay un proxy local.

### La librería `import sys`
Termina el programa ante un error en la introducción de datos del usuario.
1. `sys.exit(1)`: Se aplica el modulo sys y su función exit, para salir del programa.
- `1` → Hubo algún problema o error y es por eso que el programa está saliendo.
- `0` → Una salida limpia sin errores.

### La librería `import platform` 
Saber el sistema operativo donde corremos el programa.
1. `platform.system()=="Windows"`: Se comprueba el sistema operativo que se está utilizando es windows. `system()` → Devuelve el nombre del sistema/OS, por ejemplo, 'Linux', 'Windows' o 'Java'.

### La librería `import os`
Para realizar el ping a través del sistema Operativo.
1. `response = os.popen(ping+" "+direccion)` → Se obtiene la respuesta del ping
- `ping = ping -n 1` → Número de solicitudes de eco para enviar. Se manda un solo (`-n 1`) paquete
- `ping = ping -c 1` (en UNIX) → Se manda un solo (`-c 1`) paquete. 
2. `mac = os.popen("arp -a"+" "+direccion+" "+"-v")` 
- `arp = arp -a` → Muestra la tabla de resolución de las IPs y MAC address. 

### Otras Funciones
1. `response.readlines()` → El modulo `readlines()` devuelve el contenido de todo el archivo como una lista de cadenas, donde cada elemento de la lista representa una línea del archivo.
2. `line.lower()` → Para saber si la IP está activa, comprobaremos con la respuesta `ttl` que tenemos contiene la palabra `ttl`, utilizo `line.lower()` porque parece que en Linux sale en minúsculas y en Windows en mayúsculas, así no tenemos problemas. 

### La librería `from datatime import datetime` 
Para saber el tiempo que tarda en realizar el escaneo.
1. `tiempoInicio = datetime.now()`: Se obtiene la hora correspondiente y se guarda en una variable. Se aplica la clase `datetime` y el método `now` que construye un `datetime` a partir de `time.time()` y la información opcional de la zona horaria.

