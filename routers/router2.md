# router1

## Máquina

### myname

```
router2
```

### resolv.conf

```
lookup file bind
search 7.ff.es.eu.org
nameserver 2001:470:736b:720::2
```

### ntpd.conf (client)

```
cp /etc/examples/ntpd.conf /etc/ntpd.conf
```

```
# $OpenBSD: ntpd.conf,v 1.5 2019/11/11 16:44:37 deraadt Exp $
# sample ntpd configuration file, see ntpd.conf(5)

listen on 2001:470:736b:720::2
server 2001:470:736b:720::2 trusted
query from 2001:470:736b:720::2
```

### doas.conf

```
cp /etc/examples/doas.conf /etc/doas.conf
```

```
permit nopass keepenv :wheel
```

## Red

### mygate

```
2001:470:736b:710::1
```

### hostname.vio0

```
-inet6
up
```

### hostname.vlan710

```
vlan 710 vlandev vio0 up
inet6 2001:470:736b:710::2
```

### hostname.vlan711

```
vlan 711 vlandev vio0 up
inet6 2001:470:736b:711::1
```

### hostname.vlan712

```
vlan 712 vlandev vio0 up
inet6 2001:470:736b:712::1
```

### forwarding de paquetes

Copia el archivo de ejemplo `sysctl.conf` al archivo de configuración actual:

```bash
cp /etc/examples/sysctl.conf /etc/sysctl.conf
```

Este comando copia el archivo de ejemplo "sysctl.conf" del directorio "/etc/examples/" al archivo de configuración actual "/etc/sysctl.conf". El archivo "sysctl.conf" es utilizado para establecer valores de configuración de kernel en OpenBSD.

Edita el archivo `/etc/sysctl.conf` para habilitar el forwarding de paquetes IPv6:

```
net.inet6.ip6.forwarding=1      # 1=Permit forwarding (routing) of IPv6 packets
```

Este paso modifica el archivo "/etc/sysctl.conf" para habilitar el forwarding de paquetes IPv6. Se agrega una línea que establece el valor de la variable "net.inet6.ip6.forwarding" en "1", lo que permite el forwarding de paquetes IPv6.

Comprueba que el forwarding de paquetes IPv6 está habilitado:

```bash
sysctl net.inet6.ip6.forwarding
```

Este comando muestra el valor actual de la variable "net.inet6.ip6.forwarding". Si el valor es "1", significa que el forwarding está habilitado. Si el valor es "0", significa que está deshabilitado.

Habilita el forwarding de paquetes IPv6 en tiempo real:

```bash
doas sysctl net.inet6.ip6.forwarding=1
```

Este comando establece el valor de la variable "net.inet6.ip6.forwarding" en "1" en tiempo real, lo que habilita el forwarding de paquetes IPv6 sin necesidad de reiniciar el sistema.

---

```
/etc/netstart
```
