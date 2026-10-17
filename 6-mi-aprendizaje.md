# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.

# MI APRENDIZAJE

Antes de realizar esta práctica, conocía de forma superficial que Docker permitía ejecutar aplicaciones en contenedores, pero no tenía claro cómo persistir la información ni cómo evitar que los datos se perdieran al eliminar un contenedor.

Después de completar los ejercicios, comprendí la diferencia entre bind mounts, volúmenes nombrados y volúmenes anónimos, tambien aprendí que los bind mounts dependen de una ruta del host y que los cambios son inmediatos, mientras que los volúmenes nombrados son gestionados por Docker y son más portables y fáciles de respaldar.

También aprendí a crear redes personalizadas en Docker para que los contenedores se comuniquen por nombre, sin necesidad de usar direcciones IP, esto fue importante para conectar WordPress con MySQL y Drupal con PostgreSQL.

Además, practiqué la creación de volúmenes nombrados para PostgreSQL y para las carpetas de Drupal (modules, profiles, themes, sites), lo que me permitió entender qué rutas dentro del contenedor deben persistirse según la documentación de cada imagen.

Un problema que encontré fue que al montar una carpeta vacía en Nginx, el index.html original desaparecía. Lo solucioné descargando un template y colocándolo en la carpeta del host, también aprendí que los volúmenes deben configurarse al crear el contenedor y que no se pueden modificar después.

Finalmente, usé comandos como `docker volume create`, `docker volume ls`, `docker network create`, `docker run` con `-v` y `--network`, y comprendí la importancia de revisar la documentación de cada imagen en Docker Hub para conocer las rutas correctas de persistencia.
