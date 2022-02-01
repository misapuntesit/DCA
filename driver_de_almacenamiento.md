# Seleccionando un driver de almacenamiento

Los drivers de almacenamiento son frameworks para gestionar el almacenamiento interno de un contenedor. Por lo que si tienes un software en tu contenedor que necesita escribir ficheros o escribir datos en el disco duro del sistema, se escribiran en el  almacenamiento interno del contenedor a no ser que montemos un almacenamiento externo.

Los drivers permiten a docker poder soportar diferentes sistemas operativos y entornos, porque algunos de los tipos de almacenamiento solo funcionan en ciertos entornos especificos.
Por lo que dependiendo del entorno o SO en el que estemos necesitaremos un driver u otro.
Algunos drivers son mejores para ciertos casos de uso y algunos son más eficientes en algunos casos y menos eficientes en otros casos, por eso debemos conocerlos para intentar usar el que mejor nos convenga.

Podemos chequear la documentación oficial para seleccionar el mejor driver que nos convenga:

https://docs.docker.com/storage/storagedriver/select-storage-driver/

Los que nosotros necesitamos conocer ahora son el overlay2 y el devicemapper.

**Overlay2** nos ofrece **almacenamiento basado en ficheros** y actualmente es el que viene por defecto para ubuntu y centos, pero en Centos solo en la version 8 o superiores.

Por lo que para CentOS 7 y versiones anteriores, la que viene por defecto es **devicemapper** que nos ofrece **almacenamiento de bloque**

De momento nos vale con saber que **devicemapper** es un poco **mejor en el performance cuando estamos escribiendo mucho** en las capas del contenedor.
Pero si tienes que elegir entre devicemapper y overlay2, **overlay2** es mucho **mejor haciendo lecturas**, este driver nos ira bien en la mayoría de los casos pero si necesitas escribir mucho en disco quizás necesitemos devicemapper.


# Vamos a la terminal

Vamos a lanzar el siguiente comando para conocer la información del servicio docker que esta corriendo en nuestra máquina:

```bash
docker info
```

Aquí podemos ver que driver de almacenamiento esta corriendo en nuestro docker, en nuestro caso vemos que esta corriendo devicemapper porque es un CentOS 7.


