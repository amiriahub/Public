# Guia de instalación de RabbitMQ en CentOS 7.x

## Dependencia Erlang

### 1. Instalar el paquete Erlang desde Erlang Solutions

Verificar la versión desde la [documentación de RabbitMQ](http://www.rabbitmq.com/which-erlang.html). Entonces
seguir las indicaciones desde el [sitio de Erlang](https://www.erlang-solutions.com/resources/download.html). 

**Importante:** No es necesario instalar el erlang, la dependencia del RabbitMQ cargará los paquetes necesarios!

Ejemplo:

```shell
> wget https://packages.erlang-solutions.com/erlang-solutions-1.0-1.noarch.rpm
...
> rpm -Uvh erlang-solutions-1.0-1.noarch.rpm
...
```

### 2. Instalar RabbitMQ usando RPM

Fuente http://www.rabbitmq.com/install-rpm.html#with-rpm

Obtener el archivo RPM desde el sitio de RabbitMQ donde se muestran los 
[enlaces de descargas](http://www.rabbitmq.com/install-rpm.html#rpm-packages) según las versiones disponibles.

Ejemplo:

```shell
> wget https://dl.bintray.com/rabbitmq/all/rabbitmq-server/3.7.5/rabbitmq-server-3.7.5-1.el7.noarch.rpm
...
```

Antes de instalar debemos adicionar la llave de cifrado del RPM, posteriormente podremos [instalar el arhivo
rpm descargado](http://www.rabbitmq.com/install-rpm.html#with-rpm).

```shell
> yum install rabbitmq-server-3.7.5-1.el7.noarch.rpm
...
```

### 3. Habilitar el servicio RabbitMQ

Finalmente habilitamos el deamon y auto-inicio del RabbitMQ Server:

```shell
> chkconfig rabbitmq-server on
```

### 4. Controlar el servicio RabbitMQ


Inicio:
```shell
> systemctl start rabbitmq-server.service
```

Detener:
```shell
> systemctl stop rabbitmq-server.service
```

Estado:
```shell
> systemctl status rabbitmq-server.service
```