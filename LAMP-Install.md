
# Instalación Pila LAMP en CentOS 8

### Configuración Inicial del VPS

Primeramente debemos asegurarnos que nuestro VPS se encuentre actualizado utilizando el comando:

```
sudo dnf update -y
```

Una vez actualizado el VPS, procedemos a realizar la instalación de el servidor web Apache.

### Instalación APACHE

Utilizamos el comando:

```
dnf install httpd -y
```

Una vez realizado este paso, debemos iniciar el servicio de Apache utilizando el comando:
```
systemctl enable httpd
systemctl start httpd
```
Con esto, accediendo a la dirección de nuestro servidor en el navegador, observaremos una página de prueba que corrobora que Apache se ha instalado correctamente.

### Instalación de PHP
Realizaremos la instalación de PHP 7.3 para poder instalar Laravel en su versión 8. Para esto tendremos que instalar los paquetes Remi y EPEL.

```
dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm -y
```

Y posteriormente:

```
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm -y
```

Una vez instalados estos dos paquetes, procederemos a instalar la versión 7.3 de PHP con el siguiente comando:

```
dnf module install php:remi-7.3 -y
```

Por último, como requerimento instalaremos los siguientes modulos de php para evitar problemas de compatibilidad e instalación.
```
dnf install php-cli php-json php-xml php-bcmath php-gd zip unzip php-zip -y
```

Para utilizar Laravel 8 y su conexión a la base de datos, es necesario instalar el componente de MySQL para PHP, utilizando el siguiente comando:

```
dnf install php-mysqlnd -y
```

Continuar con la instalación de [Laravel 8 en CentOS 8](https://github.com/Campus-TD/documentacion/blob/main/LARAVEL-Install.md).
