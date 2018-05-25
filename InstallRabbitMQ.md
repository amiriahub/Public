# Guia de instalación de RabbitMQ en CentOS 7.x

## Dependencia Erlang

### 1. Habilitar repositorios ELEP de Fedora para instalar Erlang via YUM

Fuente http://fedoraproject.org/wiki/EPEL/FAQ#howtouse

```shell
rpm -Uvh http://download.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-10.noarch.rpm

```

### 2. Instalar Erlan usando YUM

Fuente http://www.rabbitmq.com/install-rpm.html#install-erlang-from-epel-repository

```shell
yum install erlang
...
```