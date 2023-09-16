# Image to Laravel 5.7
Se crea un directorio ./Docker-config dentro del proyecto de Laravel que quieran dockerizar ó clonan este repo y agregan este diorectorio dentro del proyecto
## Version PHP
PHP 7.4.33 (cli) (built: Nov 15 2022 06:03:30) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Xdebug v3.1.6, Copyright (c) 2002-2022, by Derick Rethans


## Version mysql
mysql  Ver 14.14 Distrib 5.7.43, for Linux (x86_64) using  EditLine wrapper


## Run
```
docker compose up -d
docker exec -ti lv_facturatec bash
docker exec -ti lv_facturatec_db bash
```