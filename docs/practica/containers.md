# Containers

## **Ejercicio 1**
---

1. Restaurar la instantánea `docker` en la maquina virtual sin resguardar ningun cambio e iniciar la VM
2. Crear una imagen basada en Ubuntu e instalar nginx desde repositorio oficial del producto
3. Correr la imagen exponiendo el puerto correspondiente y verificar su funcionamiento desde el host
4. Realizar las configuraciones necesarias a la VM para que el servicio pueda ser accedido desde la red del aula.
5. Verificar con algun compañero que el servicio de nginx puede ser accedido a traves de la red.
6. Apagar la maquina virtual y realizar una instantanea de nombre `nginx`

## **Ejercicio 2**
---

1. Restaurar la instantánea `podman` en la VM
2. Crear una imagen basada en CentOS 7 e instalar httpd del repositorio del sistema operativo
3. Correr la imagen exponiendo el puerto correspondiente y verificar su funcionamiento desde el host
4. Realizar las configuraciones necesarias a la VM para que el servicio pueda ser accedido desde la red del aula.
5. Verificar con algun compañero que el servicio de httpd puede ser accedido a traves de la red.
6. Apagar la maquina virtual y realizar una instantanea de nombre `httpd`

## **Ejercicio 3**
---

1. Restaurar la instantánea `containerd` en la maquina virtual
2. Crear una imagen basada en alpine e instalar en el mismo minio
3. Correr la imagen en el puerto por defecto de aplicacion y verificar su funcionamiento desde el host
4. Cambiar las propiedades de red de la maquina virtual para la misma poseea una dirección IP del segmento de red del aula.
5. Verificar con algun compañero que el servicio de minio puede ser accedido a traves de la red.
6. Apagar la maquina virtual y realizar una instantanea de nombre `minio`

## **Ejercicio 4**
---

1. Restaurar la instantánea `nginx` creada anteriormente
2. Crear un archivo html en el host que diga 'DevOps 2022' y montarlo en el container para que sea servido por el servidor web
3. Acceder nuevamente desde algun otra pc dentro de la red del aula

## **Ejercicio 5**
---

1. Restaurar la instantánea `httpd` creada anteriormente descartando cualquier cambio anterior
2. Crear un archivo html en el host que diga 'DevOps 2022' y montarlo en el container para que sea servido por el servidor web
3. Acceder nuevamente desde algun otra pc dentro de la red del aula

## **Ejercicio 6**
---

1. Restaurar la instantánea `minio` creada anteriormente descartando cualquier cambio anterior
2. Montar una carpeta del hots para que los datos se guarden en el host.
3. Acceder nuevamente desde algun otra pc dentro de la red del aula


## **Ejercicio 7**
---

1. Crease una cuenta en DockerHub
2. Pushear las imagenes creadas anteriormente.
3. Probarlas desde otro computador del aula


## **Ejercicio 8**
---

1. Realizar grupos de 2 personas
2. El primer integrante restaura en su PC la instantánea `docker`
3. El segundo integrante restaura en su PC la instantánea `podman` 
4. El primer integrante tiene que crear una imagen basada en Ubuntu con OpenSSH Server instalado
5. El segundo integrante tiene que crear una imagen basada en CentOS 7 con OpenSSH Server instalado
6. Ambos deben ejecutar la imagen exponiendo el servidor SSH en algun puerto de su elección
7. Ingresar cada uno por ssh desde el host al container del otro

