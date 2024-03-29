# Virtualización

## **Ejercicio 1 - Creación**
---


1. Maquina Virtual `ubuntu` 
    1. Crear una máquina virtual con las siguientes características. 
        - **Nombre:** ubuntu  
        - **CPU:** 2 cores  
        - **RAM:** 2 GB  
        - **Disco:** 20 GB
            - Formato VDI
            - Dinamicamente alocado
        - **Red:** NAT
        - **SO:** Ubuntu 20.04 LTS
    - Iniciar la maquina virtual y realizar las siguientes tareas
        - Instalar el sistema operativo Ubuntu 20.04 LTS
            - Usar particionado estandar (no LVM)
            - Durante la instalación crear el usuario `devops`
            - Usar las minimas configuraciones de instalación
            - Instalar Servidor SSH
        - Aplicar las últimas actualizaciones disponibles
        - Apagar la maquina virtual
    - Crear una instantanea de la maquina virtual llamada `init`

- Maquina Virtual `centos` 
    1. Crear una nueva máquina virtual con las siguientes características. 
        - **Nombre:** centos  
        - **CPU:** 2 cores 
        - **RAM:** 2 GB  
        - **Disco:** 20 GB
            - Formato VDI
            - Dinamicamente alocado
        - **Red:** NAT
        - **SO:** CentOS 7 
    - Iniciar la maquina virtual y realizar las siguientes tareas
        - Instalar el sistema operativo CentOS 7
            - Usar LVM durante el particionado
            - Durante la instalacion crear el usuario `devops`
            - Usar las minimas configuraciones de instalación
        - Aplicarle las ultimas actualizaciones disponibles
        - Apagar la maquina virtual
    - Crear una instantanea de la maquina virtual llamada `init`

## **Ejercicio 2 - Paquetes**
---


1. Maquina Virtual `ubuntu` 
    1. Instalar docker usando la siguiente [guía](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
        - Instalar utilizando el repositorio comunitario oficial
    - Apagar la maquina virtual y realizar una instantanea con nombre `containers`
    - Instalar Nginx utilizando los repos oficiales usando la siguiente [guía](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/#installing-a-prebuilt-ubuntu-package-from-the-official-nginx-repository)
    - Habilitar y arrancar el servicio de nginx
    - Realizar una consulta simple al servicio con curl desde el host
    - Apagar la maquina y restaurar la instantanea `containers` creando una instantanea llamada `packages` para almacenar el trabajo hecho.



- Maquina Virtual `centos` 
    1. Instalar podman usando la siguiente [guía](https://podman.io/getting-started/installation)
        - Instalar utilizando el repositorio comunitario oficial
    - Instalar CRI-O version 1.20 usando la siguiente [guía](https://github.com/cri-o/cri-o/blob/master/install.md#other-yum-based-operating-systems)
    - Apagar la maquina virtual y realizar una instantanea con nombre `containers`
    - Instalar HAProxy utilizando el repositorio los paquetes preconstruidos del sistema operativo
    - Habilitar y arrancar el servicio de HAProxy
    - Realizar una consulta simple al servicio con curl desde el host
    - Apagar la maquina y restaurar la instantanea `containers` creando una instantanea llamada `packages` para almacenar el trabajo hecho.


## **Ejercicio 3 - Red**
---

1. Iniciar las maquinas virtuales `centos` y `ubuntu`
- NAT
    - Realizar ping a internet
    - Realizar ping al host
    - Realizar ping a las otras maquinas virtuales
    - Ingresar por ssh a las maquinas virtuales
        - Intentar desde el host
        - Intentar desde las maquinas virtualess a la otra
    - Configurar port forwarding para poder ingresar por ssh desde el host
        - Configurar el puerto 1022 para la maquina `centos`
        - Configurar el puerto 1023 para la maquina `ubuntu`
- Bridge Adapter
    - Conectar las maquinas virtuales a la red LAN local de tu casa
    - Ingresar por ssh desde una maquina virtual hacia la otra
    - Ingresar por ssh desde el host
- Net Host Adapter
    - Configurar el Net Host Adapter con la IP 10.0.2.1/24, deshabilitar DHCP
    - Configurar direcciones IP estaticas en las máquinas virtuales en el segmento anterior
    - Ingresar por ssh desde una maquina virtual hacia la otra
    - Ingresar por ssh desde el host
    - Repetir con otro segmento de red
- Red NAT
    - Crear una Red NAT llamada `devops`, con DHCP activado
    - Conectar las maquinas virtuales a esta red NAT
    - Ingresar por ssh desde una maquina virtual hacia la otra
    - Ingresar por ssh desde el host usando port forwarding
    - Deshabilitar DHCP en la Red NAT
    - Configurar direcciones IPs estáticas en las maquinas virtuales.
    - Ingresar por ssh desde una maquina virtual hacia la otra
    - Ingresar por ssh desde el host usando port forwarding
- Apagar la maquina y crear instantantea con el nombre `network` 


## **Ejercicio 4 - Almacenamiento**
---

1. Maquina Virtual `ubuntu` 
    1. Con la maquina apagada agregar un nuevo disco de 2 GB
    -  Iniciar la maquina y realizar las siguientes tareas
       - Ubicar el nuevo dispositivo agregado (`/dev`)
       - Crear una nueva particion dentro del dispositivo
       - Formatear la nueva particion con formato ext4
       - Montar el nuevo file system en `/home/devops/storage`, y que permanezca durante reinicios.
       - Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `storage` para almacenar el trabajo hecho.

- Maquina Virtual `centos` 
    1. Con la maquina apagada agregar un 2 discos nuevos de 2 GB cada uno
    -  Iniciar la maquina y realizar las siguientes tareas
       - Ubicar los nuevos dispositivos agregados (`/dev`)
       - Crear una nueva particion dentro de cada dispositivo
       - Crear un pv (physical volume) a partir de las nuevas particiones
       - Crear un nuevo vg (volume group) con nombre `devops` y añadir los ultimos dos pv
       - Crear un lv dentro del vg `devops` con nombre `storage` usando todo el espacio disponible
       - Formatear el nuevo lv con formate xfs
       - Montar el nuevo file system en `/home/devops/storage`, y que permanezca durante reinicios.
       - Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `storage` para almacenar el trabajo hecho.


## **Ejercicio 5 - Usuarios**
---


1. Maquina Virtual `ubuntu` 
    1. Crear el usuario `ubuntu` y el usuario `guest`, asignarle una contraseña a cada uno
    -  Crear el grupo `frre`
    -  Agregar el usuario `ubuntu` al grupo `frre`
    -  Crear el archivo `test-user-permission.txt` y darle permisos exclusivos de lectura, escritura y ejecucion al usuario `ubuntu`
    -  Intentar acceder a este archivo como el usuario `guest`
    -  Crear el archivo `test-group-permission.txt` y darle permisos exclusivos de lectura, escritura y ejecucion al group `frre`
    -  Intentar acceder a este archivo como el usuario `guest` y con el usuario `ubuntu`
    -  Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `users` para almacenar el trabajo hecho.

- Maquina Virtual `centos` 
    1. Crear el usuario `centos` y el usuario `guest`, asignarle una contraseña a cada uno
    -  Crear el grupo `frre`
    -  Agregar el usuario `centos` al grupo `frre`
    -  Crear el archivo `test-user-permission.txt` y darle permisos exclusivos de lectura, escritura y ejecucion al usuario `centos`
    -  Intentar acceder a este archivo como el usuario `guest`
    -  Crear el archivo `test-group-permission.txt` y darle permisos exclusivos de lectura, escritura y ejecucion al group `frre`
    -  Intentar acceder a este archivo como el usuario `guest` y con el usuario `centos`
    -  Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `users` para almacenar el trabajo hecho.


## **Ejercicio 6 - SSH**
---


1. Maquina Virtual `ubuntu` 
    1. Crear una clave ssh para el usuario `ubuntu`
    -  Autorizar la clave publica generada para el usuario `centos` en la maquina virtual `centos`
    -  Ingresar por ssh con el usuario `centos` a la maquina virtual `centos` a traves de la clave generada
    -  Repetir las pruebas de permisos del ejercicio anterior
    -  Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `ssh` para almacenar el trabajo hecho.

1. Maquina Virtual `centos` 
    1. Crear una clave ssh para el usuario `centos`
    -  Autorizar la clave publica generada para el usuario `ubuntu` en la maquina virtual `ubuntu`
    -  Ingresar por ssh con el usuario `ubuntu` a la maquina virtual `ubuntu` a traves de la clave generada
    -  Repetir las pruebas de permisos del ejercicio anterior
    -  Apagar la maquina y restaurar la instantanea `network` creando una instantanea llamada `ssh` para almacenar el trabajo hecho.
