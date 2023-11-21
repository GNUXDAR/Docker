Nota: se ejecutan dentro del directorio docker
***Resumen y hoja de trucos

## List Docker CLI commands
docker  
docker container --help  

## Display Docker version and info
docker --version  
docker version  
docker info  

## Execute Docker image
docker run hello-world  

## List Docker images
docker image ls  

## List Docker containers (running, all, all in quiet mode)
docker container ls  
docker container ls --all  
docker container ls -aq  


## Aquí hay una lista de los comandos básicos de Docker

- docker build -t friendlyhello .  		# Create image using this directory's Dockerfile  
- docker run -p 4000:80 friendlyhello  	# Run "friendlyhello" mapping port 4000 to 80  
- docker run -d -p 4000:80 friendlyhello  # Same thing, but in detached mode  
- docker container ls                     # List all running containers  
- docker container ls -a             		# List all containers, even thosenot running  
- docker container stop <hash>           	# Gracefully stop the specified container  
- docker container kill <hash>         	# Force shutdown of the specified container  
- docker container rm <hash>        		# Remove specified container from this machine  
- docker container rm $(docker container ls -a -q)	# Remove all containers  
- docker image ls -a                  			  	# List all images on this machine  
- docker image rm <image id>            	# Remove specified image from this machine  
- docker image rm $(docker image ls -a -q)   		# Remove all images from this machine  
- docker login             		# Log in this CLI session using your Docker credentials
- docker tag <image> username/repository:tag  	# Tag <image> for upload to registry
- docker push username/repository:tag      		# Upload tagged image to registry
- docker run username/repository:tag   			# Run image from a registry
- docker exec -ti laravel_db2_1 bash				#terminal de docker
- docker ps 								#muestra los container ejecucion
- docker ps -a 							#muestra todos los coantainer en lista
- docker rm 								#elimina el contenedor
- docker volume 							#para ver los volumenes
- docker-compose build --no-cache           # intentar limpiar y construir de nuevo sin utilizar la caché del Dockerfile
- docker builder prune -a                      #limpiar la cache de docker

## Algunos de los comandos que he utilizado

- docker-compose --version 				#la version de docker-compose
- docker-compose version 					#mas informacion con la version
- docker-compose ps 						#muestra los contenedor

## Para corregir
- docker rm ID					(eliminar el contenedor)
- docker-compose up -d 			(ejecutar el OS)

## Abrir Terminal del contenido (modificar eqsoft)

- docker exec -ti eqsoft_centos bash     (eqsoft_centos = nombre del docker)
- vim /etc/httpd/conf.modules.d/00-base.conf  
	<Directory /var/www/html/eqsoft_etm>
	    AllowOverride All
	</Directory>


- docker exec -ti eqsoft_db2_1 bash		eqsoft_db2_1 = nombre de la img de la base de datos
	mysql -u root -p
				(clave = example "colocada en docker-compose.yml")

Copiando archivo desde / a contenedores

## Del contenedor al host
docker cp CONTAINER_NAME:PATH_IN_CONTAINER PATH_IN_HOST

## De host a contenedor
docker cp PATH_IN_HOST CONTAINER_NAME:PATH_IN_CONTAINER


# Backup
docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

docker exec eqsoft_db2_1 /usr/bin/mysqldump -u root --password=example eqsoft_dev > bk_dev.sql;

# Restore
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE

docker exec CONTAINER /usr/bin/mysqldump -u root --password=example cms_hotels > cms_restaurant.sql;

## Intento de rcear un virtual host
touch /etc/httpd/conf.d/my_virtualhost.conf

<VirtualHost *:80>
    ServerName mysite.local
    DocumentRoot /var/www/html/cms_restaurant

    <Directory /var/www/html/cms_restaurant>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>


docker exec -it tu_contenedor_apache service apache2 restart
