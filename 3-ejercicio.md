## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es (COMPLETAR CON LA RUTA)
/var/lib/mysql
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Inicialmente está vacía, porque MySQL aún no ha sido ejecutado ni ha creado sus archivos de datos.
### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
docker run -d --name server-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=wp_db -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_pass -v "C:\Users\P3E010-D\Desktop\ejercicio3\db:/var/lib/mysql" mysql:8
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Ahora contiene múltiples archivos y carpetas (ibdata1, ib_logfile, carpetas de bases de datos, etc.) creados automáticamente por MySQL.
### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (COMPLETAR CON LA RUTA)
/var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
docker run -d --name server-wordpress --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=server-mysql:3306 -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_pass -e WORDPRESS_DB_NAME=wp_db -v "C:\Users\P3E010-D\Desktop\ejercicio3\www:/var/www/html" wordpress
### Personalizar la apariencia de wordpress y agregar una entrada

<img width="3758" height="1344" alt="image" src="https://github.com/user-attachments/assets/daef0311-2236-43d0-8027-4001aee86c76" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Al eliminar y recrear el contenedor, toda la información persiste (entrada, usuario, tema) porque está guardada en el bind mount del host. WordPress detecta que ya está instalado.
