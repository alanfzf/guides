# Comandos varios

```bash
# tracert
trace [ip]
# ??? 
show ip protocols
# rutas de ospf
show ip route ospf
# configuraciones
show run
# rutas estaticas
show ip route
# indicar la direccion del servidor dhcp en los routers.
ip helper-address servidor-dhcp
```

# VLAN's
## Crear VLAN

```bash
# Se necesita estar en modo de configuracion global.
vlan [numero de la vlan a crear.]
name [nombre de la vlan]
```

## Configuración de las interfaces

```bash
# poner la interfaz f0/1 en modo access y asignarle la vlan 10
int f0/1
swi mode access
swi access vlan 10
# poner la interfaz f0/2 en modo access y asignarle la vlan 10
int f0/2
swi mode access
swi access vlan 10
# poner la interfaz f0/3 en modo access y asignarle la vlan 20
int f0/3
swi mode access
swi access vlan 20
# NOTA Debemos de replicar esta configuración en el otro switch tambien.
```

## Configuración de trunk

```bash
# Poner la interfaz en modo trunk
# se debe poner ambas interfaces en modo trunk para que exista comunicacion
int g0/0 
swi mode trunk
# Establecer las vlans permitidas 
swi trunk allowed vlan [all, 10]
# Agregar mas vlans sin eliminar las demas.
swi trunk allowed vlan add 20
```

## Mover interfaces de la vlan predeterminada.

```bash
# Crear la vlan 99
vlan 99
# Nombrar la interfaz
name admin
# Seleccionar un rango interfaces de la 4 a la 24.
int range f0/4 -24
# Establecer el modo de la interfaz
swi mode access
# Establecer la vlan 
swi mode vlan 99
```

# Dot1Q

```bash
# la interfaz del switch que va conectada al router debe estar en modo trunk.
# del switch se conecta al router con interfaz g0/0 o la interfaz padre en 
# este caso g0/0
int g0/0.10

int g0/0.20

# dotq1 
swi trunk encapsulation dot1q

# encapsulacion de las vlans.
encapsulation dot1q <id de la vlan>
encapsulation dot1q 10
encapsulation dot1q 20
```

# OSPF

## Configuración básica

```bash
# Entrar en la configuración de OSPF
router ospf 1 
# Aqui agregamos un id debe ser como una ip ejemplo: 3.3.3.3
router-id [id]
# Ejemplo network 192.168.100.1 0.0.0.255 area 0
# Aqui debemos de definir cada una de las redes que deseemos compartir.
network [ip] [mascara de subred inversa] area [num]
# Eliminar anuncio de una network
no network [ip] [mascara de subred inversa] area [num]
```

## Status de OSPF

```bash
# Configuracion general
show run

# verificar los vecinos de ospf
show ip ospf neighbor

# verificar la base de datos de ospf
show ip ospf database

# Ayudas
# Para cuando los temporizadores no cazan (hello y dead)
show ip ospf interface

# Checar que esten en la misma area
# Los RID deben ser unicos
show ip ospf interface brief

# Autenticacion entre vecinos
show ip ospf interface

# OSPF no debe estar apagado
show ip ospf 
show ip ospf interface
```

# EIGRP 

## Configuración básica

```bash
router eigrp 1
# este debe ser diferente para cada router.
eigrp router-id 1.1.1.1
# subred
network 10.10.10.0 0.0.0.3
network 172.16.21.0 0.0.0.255
# mostrar los vecinos
show ip eigrp neighbors
```

# BGP

## Configuración inicial

```bash
# iniciar la configuracion
router bgp ['area autonoma']
router bgp 300
# indicar los vecinos
neighbor 10.10.40.1 remote-as 200
# indicar la network
network 192.168.40.0 mask 255.255.255.0
```

## Redistribuir la red

### Modo BGP

```bash
# para distribuir las redes directamente conectadas al router
redistribute connected
# para distribuir eigrp
redistribute eigrp 1
# para distribuir ospf
redistribute ospf 1
```

### Modo OSPF

```bash
# esto se hace en el modo de OSPF
# es decir `router ospf 1`
redistribute bgp ['sistema autonomo'] subnets
redistribute bgp 100 subnets
```

### Modo EIGRP

```bash
# esto se hace en el modo eigrp
# es decir `router eigrp 1`
redistribute bgp ['sitema autonomo'] metric 100 1 255 1 1500
```

# NAT

```bash
show ip nat translations
# comando 1
ip nat inside source static 192.168.0.5 172.14.0.3
# para indicar donde es el inside
ip nat inside
# para indicar hacia donde se redirige el trafico
ip nat outside

# necesita una ruta para salir
ip route 0.0.0.0 0.0.0.0 172.14.0.1
```

```bash 
# nat varias
ip nat pool POOL1 172.14.0.4 172.14.0.6 netmask 255.255.255.248
access-list 1 permit 192.168.0.0 0.0.0.255
ip nat inside source list 1 pool POOL1
```

```bash
# nat sobrecargada
ip nat inside source list 1 interface s0/1/1 overload
```
