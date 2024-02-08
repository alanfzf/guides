# Comandos Linux

1. [Navegación](#navegación)
2. [Administración de archivos/directorios](#administración-de-directorios-y-archivos)
3. [Administración de permisos](#administración-de-permisos)
4. [Administración de usuarios](#administración-de-usuarios)
5. [Administración de grupos](#administración-de-grupos)
6. [Procesos](#procesos)
7. [Swap](#archivos-swap)

## Navegación

### Navegación de directorios

```bash
cd [directorio]
```
#### Tipos de directorios
  - `/` _Atajo para dirigirse a root_
  - `~` _Atajo para dirigirse a home_
  - `-` _Volver al directorio previo_
  - `..` _Moverse un directorio arriba_
  - `../../` _Moverse dos directorios arriba_

### Listar contenido de un directorio

```bash
ls -[opciones]
```
#### Opciones disponibles
  - `-l` _Visualizar archivos a manera de lista con información extra como los permisos_
  - `-a` _Visualizar los archivos ocultos_

## Administración de directorios y archivos

### Creación de directorios

```bash
mkdir [opciones] [directorio]
```
#### Opciones disponibles
- `-p` _Nos permite crear directorios en cadena por ejemplo /archivos/música/_


### Copiar archivos

```bash
cp -[opción] [archivo] [destino]
```
#### Opciones disponibles
 - `-a` _Preserva todos los atributos del archivo_
 - `-b` _Realiza una copia de seguridad antes de copiar_
 - `-i` _Solicita confirmación antes de sobreescribir un archivo_
 - `-r` _Copia los archivos recursivamente_
 - `-v` _Muestra información detallada mientras realiza la copia_

### Borrar archivos

```bash
rm -[opción] [archivo]
```
#### Opciones disponibles
  - `-f` _Elimina los archivos sin pedir confirmación_
  - `-i` _Solicitar confirmación antes de eliminar el archivo/s_
  - `-r` _Nos permite eliminar recursivamente (útil para borrar directorios)_
  - `-v` _Muestra información de cada archivo que se elimina_

## Administración de permisos

### chmod

```bash
chmod [grupo] [+/-][permiso] [archivo/directorio]

#NOTA: Si necesitamos aplicar los permisos de manera recursiva a un directorio
#podemos anteponer el parámetro -R al comando para que los permisos se apliquen
#a todos los archivos del directorio.
```
#### Tipos de grupos 
 - `u` _Usuario_
 - `g` _Grupo_
 - `o` _Otros/Todos_

#### Tipos permisos
 - `r` _Lectura_
 - `w` _Escritura_
 - `x` _Ejecución_

### chown

Este comando nos permite cambiar el propietario del archivo

```bash
chown [usuario] [archivo]
```

## Administración de usuarios

### Crear usuario
```bash
#Este comando nos permite crear un usuario con el asistente
adduser
#Este comando alternativo nos permite especificar ciertos parámetros cuando creemos al usuario
useradd
```

### Modificar datos de un usuario

```bash
usermod -[opciones] [usuario]
```
#### Opciones disponibles
  - `-c` _Agrega o modificar el comentario del usuario_
  - `-d` _Modifica el directorio home del usuario_
  - `-e` _Modifica o establece la fecha de expiración de la cuenta_
  - `-g` _Modifica el grupo principal de usuario_
  - `-G` _Establece los otros grupos a los que puede pertenecer el usuario_
  - `-l` _Modifia el nombre del login_
  - `-L` _Bloquea la cuenta del usuario_
  - `-u` _Modifica el UID del usuario_
  - `-U` _Desbloquea la cuenta del usuario_

### Modificar o establecer contraseña de un usuario

```bash
passwd [usuario]
```

### Eliminar un usuario

```bash
userdel -[opciones] [usuario]
```
#### Opciones disponibles
  - `-r` _Elimina el directorio home del usuario_
  - `-f` _Forzar a eliminar los archivos del usuario_

## Administración de grupos

### Crear un grupo

```bash
groupadd [nombre]
```
### Modificar un grupo

```bash
groupmod -[opcion] [cambio] [nombre_grupo]
```
#### Opciones disponibles
  - `-g` _Modifica el id del grupo_
  - `-n` _Modifica el nombre del grupo_

### Agregar usuario a un grupo

```bash
adduser [usuario] [grupo]
```
### Remover usuario de un grupo

```bash
deluser [usuario] [grupo]
```
### Cambiar grupo de un archivo

```bash
chgrp [groupo] [archivo]
```
## Procesos

### Comando para visualizar procesos

```bash
ps -[opciones]
```
#### Opciones disponibles
  - `-A` _Visualizar todos los procesos_
  - `-a` _Visualizar todos los procesos_
  - `-e` _Visualizar todos los procesos_
  - `-p` _Filtrar por id de proceso_
  - `-f` _Despliega toda la información_
  - `-x` _Procesos que están funcionando_

### Visualizar los procesos a manera de árbol

```bash
pstree
```
### Visualizar los procesos en tiempo real
```bash
top
```
### Modificar la prioridad a un proceso

```bash
sudo renice [prioridad] [id_proceso]

#Nota la prioridad de los procesos va de -20 a -20
#donde "-20" es la prioridad máxima y 20 es la prioridad mínima
```

### Ejecutar señales a un proceso

```bash
kill [señal] [id_proceso]
```
### Señales disponibles
  - `-l` _Lista todas las señales disponibles_
  - `-19` _Parar un proceso_
  - `-18` _Continuar un proceso_
  - `-9` _Terminar un proceso_

## Archivos Swap

### Administración de archivos swap

```bash 
#Crear un archivo swap de 0.5 GB, cabe destacar 
#que al crear el archivo swap lo hacemos con kilo bytes
#es por eso que count es 512000.
dd if=/dev/zero of=/file.swap bs=1024 count=512000
mkswap /file.swap 512000

#swapon nos permite activar el archivo swap
swapon /file.swap

#swapoff nos permite desactivar el archivo swap
swapoff /file.swap
```
### Visualizar particiones swap

```bash 
more /proc/swaps/
```