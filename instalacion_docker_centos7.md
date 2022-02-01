# Instalación Docker en Centos7

En este apunte vamos a detallar paso a paso como instalar Docker Comunity Edition en un servidor CentOS.
Este apunte se va a realizar sobre un servidor con CentOS  7, por lo que si quieres seguir esta guía necesitaras una máquina con CentOS 7.


## Instalar paquetes necesarios

El primer paso es intalar algunos paquetes requeridos por docker

```Bash
## Usamos el flag -y para evitar que nos pida aceptación
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

## Añadir el repositorio Docker

Antes de instalar el motor de docker necesitamos configurar un repositorio oficial para poder descarnaos docker. Después podremos instalar y actualizar docker desde el repositorio.

Para ello lanzamos el siguiente comando en nuestra terminal.

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Ahora ya si podemos instalar docker

En estos apuntes vamos a estar usando la versión comunity edition en la versión **docker 18.09.5** también necesitamos instalar la **docker-ce-cli** en la misma versión.

Lanzamos los siguientes comandos en nuestra terminal para instalar esta versión de docker, necesitamos instala containerd.io en este caso nos da igual la versión.

```bash
sudo yum install -y docker-ce-18.09.5 docker-ce-cli-18.09.5 containerd.io
```  

## Arrancar y habilitar el servicio de docker

Vamos a arrancar el servicio de docker y lo vamos habilitar en el arranque para que cada vez que reiniciemos nuestro servidor docker arranque automaticamente.

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

## Configurar nuestro usuario para poder usar el servicio docker

Por defecto cuando instalamos docker solo puede usar el servicio el usuario **root** lo que vamos ha realizar con los siguientes comandos es permitir que nuestro usuario pueda usarlo.

Si lanzamos el siguiente comando veremos la versión de docker que hemos instalado

```bash
sudo docker version
```
Si lanzamos el anterior comando sin **sudo** nos dara permiso denegado, para soluionarlo lanzaremos el siguiente comando:

**NOTA:** Mi usuario es **cloud_user** en tu caso deberas cambiar **cloud_user** por tu usuario.

```bash
sudo usermod -a -G docker cloud_user
```

Para que este cambio tenga efecto necesitamos reiniciar nuestra sesión para poder hacer uso del cambio anterior.

Para ello salimos o cerramos nuestra terminal y la volvemos a abrir, en mi caso voy a salir con el siguiente comando:
```bash
exit
```

Una vez reiniciada nuestra sesión podemos ver la versión de docker con nuestro usuario

```bash
docker version

#Con el siguiente comando podemos ver que nuestro usuario esta en nuestro grupo

id

```


## Arrancar nuestro primer contenedor de prueba

Para verificar que docker esta corriendo en nuestro sistema y que todo esta funcionando vamos a levantar nuestro primer contenedor de prueba.

Lanzamos el siguiente comando y levantaremos el contenedor **hello-world** :wink:

```bash
docker run hello-world
```

En este momento docker descargará la imagen del contenedor y nos ejecutará un contenedor con la imagen descargada.


Ya estamos preparados para continuar aprendiendo todo el ecosistema docker :wink:
