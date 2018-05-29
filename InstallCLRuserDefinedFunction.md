# Habilitar función CLR en SQL Server

## 1. Configurar SQL para habilitar las funciones CLR

```sql
sp_configure 'show advanced options', 1
go
reconfigure
go

sp_configure 'clr enabled', 1
go
reconfigure
go
```

## 2. Configurar la BBDD para permitir ensamblados sin firma digital

```sql
alter database [BBDD] set trustworthy on
go
```
En este caso la **BBDD** se reemplaza por el nombre la base de datos donde deseamos 
añadir la función.

## 3. Agregar los ensamblados (DLL) a la BBDD.

```sql

create assembly CLR4AMQP authorization dbo
from 'C:\Temp\DatabaseCLR4AMQP.dll'
with permission_set = unsafe
go
```
Se asume la existencia de la carpeta "Temp" donde previamente se copiarán la DLL de la función además
de todas las DLL de las cuales depende la función.

Una vez añadidas las DLL a la BBDD, las copias locales no son necesarias.

Si fuece necsario actualizar la función con una nueva versión, se debe volver a ejecutar las sentencias
provistas arriba, referenciando la dirección de la nueva DLL.

## 4. Crear la función apuntada a los ensamblados binarios.

```sql
create function AmqpExchangeSend(@uri NVARCHAR(1024), @exchangeName NVARCHAR(1024), @routingKey NVARCHAR(1024), @message NVARCHAR(1024))
returns int
as external name CLR4AMQP.UserDefinedFunctions.AmqpExchangeSend
go
```

Notar que el nombre "CLR4AMQP" fue definido en el paso 3, mientras que el resto del nombre es definido en
la programación de la función, los cuales corresponden al nombre de la clase y el nombre de la función 
definidas desde la codificación en C#.