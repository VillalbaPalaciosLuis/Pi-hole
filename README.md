# Proyecto final
## Luis Villalba Palacios
##### 2º ASIR A

**Proyecto final del grado superior de Administración de Sistemas Informáticos en Red**

## Servidor DNS con Pi-hole


![](https://upload.wikimedia.org/wikipedia/en/thumb/1/15/Pi-hole_vector_logo.svg/120px-Pi-hole_vector_logo.svg.png)

### Manual de usuario
Para ejecutar Pi-hole a través de un contenedor tenemos que crear un archivo 'docker-compose.yaml' con los siguientes parámetros:

	version: "3"

	services:
 	 pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "80:80/tcp"
      - "443:443/tcp"
    environment:
      TZ: 'Europe/Madrid' 
    volumes:
       - './etc-pihole/:/etc/pihole/'
       - './etc-dnsmasq.d/:/etc/dnsmasq.d/'
    dns:
      - 127.0.0.1
      - 1.1.1.1
    cap_add:
      - NET_ADMIN
    restart: unless-stopped

Ejecutamos el contenedor con el comando docker-compose up -d y accedemos a la terminal del contenedor para cambiar la contraseña de administración de pi-hole con el comando sudo pihole -a -p



En nuestro equipo accedemos al navegador y ponemos la dirección localhost/admin para acceder a la administración de Pi-Hole.
