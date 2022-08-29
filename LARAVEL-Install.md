
# Instalación Laravel 8 en CentOS 8

### Instalación de Composer

Para poder crear un proyecto en laravel requerimos la instalación de **Composer** *(Administrador de Paquetes)* descargando el mismo de la siguiente manera:

```
curl -sS https://getcomposer.org/installer | php
```

Una vez realizado esto, debemos mover dicho archivo descargado a la siguiente carpeta: 

```
mv composer.phar /usr/local/bin/composer
```

Y para finalizar, debemos otorgar los permisos de acceso a dicho archivo

```
chmod +x /usr/local/bin/composer
```

Con esto tendremos instalado **Composer**, lo cual nos permitirá instalar Laravel, accediendo a la carpeta raiz del Apache:
```
cd /var/www
```
Y posteriormente utilizando el comando:
```
composer create-project laravel/laravel nombreProyecto
```
Con esto tendremos creado nuestro proyecto en una carpeta con el nombre que seleccionamos. Para poder configurar nuestro proyecto, debemos acceder a la carpeta utilizando el comando:
```
cd /var/www/myLaravelApp
php artisan key:generate
```

Una vez completado este proceso, 	podremos testear nuestra aplicación lanzandola de manera local con el comando:

```
php artisan serve --host 0.0.0.0 --port=8000
```

Una vez realizado este proceso, podremos acceder a dicha aplicación desde el navegador con la IP pública de nuestro servidor/computadora, por ejemplo:
```
http://127.0.0.1
```
Posterior a esto, debemos configurar el servidor Apache para poder mostrar el proyecto desde nuestra IP, utilizando vim o el editor de texto de preferencia:

```
vi /etc/httpd/conf.d/laravel.conf
```

Pegamos el siguiente código en el archivo:

```
<VirtualHost *:80>
       ServerName laravel.example.net
       DocumentRoot /var/www/myLaravelApp/public

       <Directory /var/www/myLaravelApp>
              AllowOverride All
       </Directory>
</VirtualHost>
```

Posteriormente reiniciamos el servidor con el comando
```
systemctl restart httpd.service
```
