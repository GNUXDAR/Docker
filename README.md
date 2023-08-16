![docker](https://raw.githubusercontent.com/GNUXDAR/Docker/main/img/env.png)

1. **Comprender qué es Docker y cómo funciona**:
   Docker es una plataforma de virtualización de contenedores que te permite empaquetar, distribuir y ejecutar aplicaciones junto con sus dependencias en un entorno aislado llamado "contenedor". Los contenedores son ligeros, portátiles y consistentes en diferentes entornos. A diferencia de las máquinas virtuales, los contenedores comparten el sistema operativo del host, lo que los hace más eficientes y rápidos. Docker simplifica la implementación y gestión de aplicaciones, ya que elimina las diferencias entre los entornos de desarrollo y producción.

2. **Familiarizarte con los términos clave**:
   - **Imágenes**: Son plantillas de solo lectura que contienen una aplicación y sus dependencias. Las imágenes se utilizan como base para crear contenedores.
   - **Contenedores**: Son instancias en ejecución de imágenes. Cada contenedor es un entorno aislado que contiene todo lo necesario para ejecutar una aplicación, incluidos el código, las bibliotecas y las configuraciones.
   - **Dockerfile**: Es un archivo de configuración de texto que contiene una serie de instrucciones para construir una imagen. Define cómo se configura y se empaqueta una aplicación en una imagen.
   - **Docker Compose**: Es una herramienta para definir y orquestar aplicaciones multi-contenedor. Permite describir la configuración y las relaciones entre los contenedores en un archivo YAML.
   - **Docker Hub**: Es un registro en línea de imágenes de Docker preconstruidas y listas para usar. Puedes encontrar imágenes públicas y privadas en Docker Hub.  
  
3. **Ventajas de Docker**:  
   Flexible  
   Ligero  
   Intercambiables  
   Portatil  
   Escalable  
   Apilable  

4. **¿Que diferencia tiene con una máquina vitual?**
   Basicamente seria el peso, se pueden tener varios c ontenerdores sin si quiera refelejar su consumo de resursos.

5. **Comandos comunes**
   - $ docker -v     (version de docker)
   - $ docker        (lista de comandos)
   - $ docker info   (informacion de los contenedores)
   - $ docker info --format "{{json .}}"  (informacion en formato JSON)
   - $ docker images
   - $ docker image ls  (lista de imagenes)
   - $ docker image rm [nombre-image]     (elimina una imagen particular)
   - $ docker image rm $(docker ps -a-q)  ("expancion de comandos", elimina todas las imagenes)
   - $ docker ps -a                       (lista todos los contenedores existentes)
   - $ docker stop [nombre-contenedor]    (detiene un contenedor)
   - $ docker stop $(docker ps -a-q)      (detiene todos los contenedores)
   - $ docker logs                        (muetsra el log de los contenedores)
   - $ docker start [nombre-contenedor ó ID]   (iniciar un contenedor)
   - $ docker rm [nombre-contenedor ó ID]       (eliminar un contenedor detenido)
   - $ docker rm -f [nombre-contenedor ó ID]    (forzar eliminado de contenedor)  
  
  
6. **Descargar imagen y correr contenedores**  
   - $ docker pull [nombre-imagen]  
   - $ docker run -p 8080:80 nginx            **(construye un contenedor, empareja el puerto 8080 del host con el 80 del contenedor y contruyelo a patir de NGINX)**
   - $ docker run -p 8080:80 -d nginx     (Ejecutar contenedor en segundo plano e imprimir ID de contenedor "detach")
   - $ docker run --name my-site -p 8080:80 -d nginx  (agregar un nombre a un contenedor)  
   - $ docker rename my-site arturocabrera.com        (viejo nombre - nuevo nombre)  
   - $ docker run -it ubuntu              (contener con imagen base de ubuntu y -it interecativo "entra al contenedor")
   - $ docker run -dt ubuntu              (mantener contenedores y que no se eliminen "ejemplo para dev")  
   - $ docker exec my-site ls
   - $ docker cp index.html my-site:/usr/share/nginx/html/index.html    (copiado el fichero index.html al contenedor de nginx para ejecutarlo desde el contenedor)
   - $ docker exec -it my-site bash    (entrar al contendor: cd /usr/share/nginx/html/)
   - $ docker cp my-site:/usr/share/nginx/html/index.html index.html    (copiado el fichero index.html del contenedor de nginx al host)


7. **Aprender sobre la arquitectura cliente-servidor de Docker**:
   Docker sigue una arquitectura cliente-servidor, donde:
   - El **cliente Docker** es la interfaz de línea de comandos o la API que los usuarios utilizan para interactuar con Docker. Puede ejecutarse en la misma máquina que el servidor Docker o en una máquina remota.
   - El **servidor Docker** es el componente que administra las imágenes, los contenedores y las operaciones. Escucha las solicitudes del cliente Docker y gestiona los recursos del sistema para crear y ejecutar contenedores.

En resumen, estos conceptos fundamentales son esenciales para comprender cómo Docker permite crear entornos aislados y portátiles para tus aplicaciones, lo que simplifica el desarrollo y la implementación en diferentes entornos.