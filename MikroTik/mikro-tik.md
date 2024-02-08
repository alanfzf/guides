# Comandos varios

```bash
# acceder a la consola
/system console

# cambiar el nombre y la clave
/system identity set name=<Nombre>

# Hacer un traceroute
/tool traceroute <direccion ip>

# Hacer ping
/ping <direccion ip>
```

# Comandos print

```bash
# Imprimir la version
/system/resource/print

# Imprimir las routas
/ip route print

# Imprimir las interfaces ospf
/routing ospf interface print

# Imprimir los vecinos
/routing ospf neighbor print
/ip neighbor print
```

# Configuración de interfaces

```bash
# Agregar ip's
/ip address add address=0.0.0.0/24 interface=ether1

# Desactivar/activar una interfaz
/interface ethernet [enable/disable] ether1
```

# Configuración de OSPF 

## (ROSv6)

```bash
# visualizar las instancias
/routing ospf instance
print

# visualizar las areas
/routing ospf area
print

# visualizar y agregar las interfaces
# agregamos todas las interfaces del router.
/routing ospf interface
print 
add interface=ether1

# agregar la network a OSPF
/routing ospf network 
print
add area=backbone network=10.10.10.0/30
```

## (ROSv7)

```bash
# Crear la instancia
/routing/ospf/instance
add name=nombre_instancia router-id=1.1.1.1

# Crear el area
/routing/ospf/area
add name=nombre_area area-id=0.0.0.0 instance=nombre_instancia

# Activar ospf
/routing/ospf/interface-template
add network=10.10.10.0/30 area=nombre_area
```


```bash
# crear la instancia
/routing ospf instance
add name=ospf-instance1 originate-default=always router-id=1.1.1.1

# crear el area
/routing ospf area 
add instance=ospf-instance1 name=backbone area-id=0.0.0.0

/routing ospf interface-template
add area=backbone interfaces=ether1 networks=10.10.10.0/30 type=ptp
```