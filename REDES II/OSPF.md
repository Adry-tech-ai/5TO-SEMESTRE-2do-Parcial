# INFORMACION BASICA
- LSA: contiene información de enrutamiento.
- VIRTUAL LINK: conector que realizas contra el area de backbond.
## OSPF DE AREA SIMPLE
- Distancia administrativa: 110.
- Es el protocolo por defecto que siempre se va a utilizar.  
  ` R1(config)#ROUTER OSPF 1 `
  - Da igual en numero de proceso (puedes usar distintos en los router no es como en EIGRP)
# OSPF de área 5

**Open Shortest Path First (OSPF)**  
Es un protocolo de enrutamiento estándar que es utilizado por muchos dispositivos de red.

## Tipos de paquetes de OSPF

- **Saludo (Hello)**: se usa para descubrir y mantener vecinos.
- **DBD (Database Descriptor)**: descriptor que controla la base de datos.
- **Solicitud de enlace (Link State Request)**: se genera al principio para solicitar información.
- **Actualización (Link State Update)**: sirve para actualizar los registros de la base de datos.

## Características

- El **paquete Hello** se envía cada **30 segundos**.
- El **tiempo de espera (Dead Interval)** es de **120 segundos**.
- La **distancia administrativa** de OSPF es **110**.

## Dirección multicast

Los mensajes de saludo se envían mediante la dirección multicast:

`224.0.0.5`

## ID de acceso

El **ID de proceso** puede tener valores desde:

`1 hasta 65535`
