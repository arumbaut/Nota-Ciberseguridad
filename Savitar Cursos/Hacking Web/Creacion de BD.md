Activamos Maria DB para hacer pruebas

```
service mariadb start

Como sudo 

mysql -uroot

Nos conectamos a MDB


```

Comandos en SQL

```
show databases;

Drear BD
create database Name;

Usar la BD
use NameDatabase;

Crear una tabla
create table users(id int auto_increment primary key,username varchar(32),password varchar(32));

Insertar datos 
insert into users(username,password) value(savitar,savitar123);

Mostrar las tabals de la BD 
show tables;

Ver la estructura de una tabla
describe users;

Seleccionar datos de una tabla pues unaconsulta SQL SELECT 



```