# Orquestación de Containers

## **Ejercicio 1 - Crear Cluster Kubernetes** 
---

### Configurar Red

1. Crear una red NAT en el segmento 10.0.2.0/24
2. Compartir la conexion de internet con el adaptador asociado

> Partir de las vms Ubuntu y CentOS creadas en los TPs anteriores

### Configurar Master

1. Elegir entra la vm `ubuntu` y `centos` para el master
2. Clonar la VM elegida como `master`
3. Configurarle 2 CPUs
4. Actualizar Sistema Operativo
5. Configurar iptables
6. Configurar el Container Runtime
7. Instalar Kubeadm
8. Configurar el cgroup driver para usar systemd
9. Disable Swap
10. Configurar red y configurar el adaptador de red para que sea NAT Network con la red creada anteriormente
    -   Direccion IP: 10.0.2.10
    -   Hostname: `master`
11. Ejecutar `kubeadm config images pull`
12. Ejectuar `kubeadm init phase preflight` para validar la instalación
13. Apagar la VM
14. Crear un Snapshot de la vm llamada `kube`

### Configurar Worker

1. Clonar la vm restante como `worker`
2. Configurarle 2 CPUs
3. Configurar iptables
4. Configurar el Container Runtime
5. Instalar Kubeadm
6. Configurar el cgroup driver para usar systemd
7. Disable Swap
8. Configurar red y configurar el adaptador de red para que sea NAT Network con la red creada anteriormente
  -   Direccion IP: 10.0.2.11
  -   Hostname: `worker`
9. Ejecutar `kubeadm config images pull`
10. Ejectuar `kubeadm init phase preflight` para validar la instalación
11. Apagar la VM
12. Crear un Snapshot de la vm llamada `kube`

### Crear Cluster

1. Prender las vms
2. Verificar conexion de red entre el host y las vms
3. Verificar conexion de red entre las vms
4. Configurar el archivo host en las vms como en tu pc con el nombre k8s a la ip 10.0.2.10
5. En la vm `master` ejecutar `kubeadm init` con los parametros necesarios para llegar por el nombre k8s
6. En la vm `worker` ejecutar `kubeadm join` con los parametros necesarios para llegar por el nombre k8s

### Verificación

1. Copiar el kubeconfig a la pc e intentar hacer consultas con `kubectl`
2. Realizar consultas a la API directamente con curl, usando tokens y certificados


## **Ejercicio 2**
---

1. Clonarse el siguiente repositorio: [web-go](https://github.com/nelsonyaccuzzi/web-go.git)
2. Analizar el codigo y el Dockerfile
3. Construir la imagen y pushearla a un repo propio en dockerhub
4. Testear la imagen localmente con docker
5. Generar los siguientes recursos necesarios para ejecutar esta servidor web en Kubernetes teniendo en cuenta lo siguiente:
	- Los recursos tienen que estar en un namespace independiente
	- Las variables de ambiente `FOO` y `BAR` deben ser montadas mediante ConfigMaps en el despliegue
	- Las variables de ambiente `SUPERSECRETUSER` y `SUPERSECRETPASS` deben ser montadas mediante Secrets en el despliegue
	- Deben haber al menos dos pods corriendo
	- Se debe poder acceder a estos recursos por Ingress
6. Teniendo en cuenta lo armado, duplicar los recursos teniendo en cuenta lo siguiente
	- Los recursos tienen que estar en un namespace distinto al anterior
	- Se debe poder acceder a los servicios de este namespace por un path distinto al anterior
7. Modificar el archivo `web.go` agregando un nueva impresion por pantalla
8. Construir la imagen y pushearla con un tag nuevo (ej. `v2`)
9. Modificar los recursos necesarios para que kubernetes despliegue la nueva version.
