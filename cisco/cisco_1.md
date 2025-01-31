# Comandos de CISCO

1. [Configuración general](#configuración-general)
2. [Almacenamiento de configuración](#almacenamiento-de-la-configuración)
3. [TFTP](#tftp)
4. [Administración de interfaces](#administración-de-interfaces)
5. [Comandos show](#comandos-show)
6. [SSH](#configuración-de-ssh)
7. [DHCP](#configuración-de-dhcp)

## Configuración general
- _Establecer nombre a un dispositivo_
```
hostname [nombre]
```
- _Establecer un mensaje de bienvenida_
```
banner motd "mensaje de bienvenida"
```
- _Proteger la consola_ 
```
line console 0
password 
login
```
- _Encriptar las claves_

```
service password-encryption
```
## Almacenamiento de la configuración
- _Guardar la configuración_
```
do write
```
- _Borrar la configuración_
```
write erase
```
- _Recargar la configuración_ 
```
reload
```

## TFTP
- _Guardar la configuración actual al servidor TFTP_
```
copy running-config tftp
```
- _Cargar archivo de configuración del servidor TFTP al dispositivo_
```
copy tftp running-config
```

## Administración de interfaces
- _Entrar en modo de configuración de interfaz_
```
int [g0/0, f0/0, vlan1]
```
- _Establecer IP y máscara de subred_
```
ip add [192.168.0.1] [255.255.255.0]
```
- _Establecer la puerta de enlace predeterminada_
```
ip default-gateway [192.168.0.1]
```
- _Iniciar la interfaz_
```
no shutdown
```
- _Establecer la velocidad del dispositivo_
```
speed [auto/número]
```
- _Establecer el modo del duplex_
```
duplex [half/full/auto]
```

## Comandos Show
- _Visualizar comandos utilizados recientemente_
```
show history
```
- _Visualizar la versión de CISCO_
```
show version
```
- _Visualizar la configuración actual_
```
show running-config
```
- _Visualizar información de todas las interfaces_
```
show interfaces
```
- _Visualizar información resumida de todas las interfaces_
```
show ip int brief
```
- _Visualizar el estado de las interfaces_

```
show int status
```
- _Visualizar el estado de las Vlans_
```
show vlan
```
- _Visualizar información de una interfaz especifica_
```
show int [g0/0,f0/0, etc]
```

## Configuración de SSH
_Los pasos necesarios para poder habilitar la administración remota son:_
1. Establecer un nombre al dispositivo
2. Indicar un nombre de dominio
3. Generar una clave RSA
4. Indicar la versión de SSH
5. Habilitar conexión virtual 
6. Indicar el modo de transporte puede, ser telnet, SSH o ambos
7. Crear un usuario y clave para la conexión remota
8. Crear una clave para el EXEC privilegiado

```
hostname [nombre]
ip domain-name [mi.dominio.com]
crypto key generate rsa
ip ssh version 2
line vty 0 4 
transport input [all, ssh, telnet]
login local
username [nombre] password [clave]
enable secret [clave]
```
__*NOTA:*__ *Al configurar un switch debemos de iniciar la vlan para poder conectarnos remotamente*

## Configuración de DHCP
- _Configuración de servicio DHCP local_
```
ip dhcp pool [nombre]
default-router [192.168.0.1]
network [192.168.0.0] [255.255.255.0]
dns-server 8.8.8.8
ip dhcp excluded-address [192.168.0.1]
```
- _Establecer un servidor de DHCP externo_ 
```
ip helper-address [192.168.0.10]
```