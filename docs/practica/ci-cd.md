# CI-CD

## **Ejercicio 1**
---


1. Descargar la siguiente maquina virtual
2. Desplegar la maquina virtual en virtualbox
3. Validar la instalación y el repo tuto creado 
4. Intentar realizar un nuevo despliegue
5. Forquear el repo y crear un nuevo pipeline a partir del mismo. Validarlo.
6. Modificar el pipeline para que podman ejecute la imagen hello world
7. Modificar el pipeline para que kubectl pueda consultar el estado del cluster K8s.
8. Crear una imagen con el paquete `fortune` adentro, configurar el pod template con el nuevo container y luego agregarlo al pipeline para que se ejecute

## **Ejercicio 2**
---


1. Crear un Pipeline (a partir de un Jenkinsfile) que compile el dockerfile del siguiente proyecto https://github.com/nelsonyaccuzzi/web-go-public
2. Crear un container que tenga solo el binario de kubectl, pushearlo a dockerhub
3. Agregar el container al pod template que anteriormente creamos
4. Crear un pipeline que haga un `kubectl get pod` del cluster actual (es necesario pasar los parametros `-s` `--token` `--insecure-skip-tls-verify` con sus respectivos valores)
5. Crear un pipeline que cuando se ejecute en la rama develop haga el build de una imagen de docker anterior, y cuando este en la rama master haga un `kubectl get pod` del cluster
6. Crear un pipeline que cuando se ejecute en la rama develop haga el build de la imagen y lo pushee a dockerhub
7. Crear un pipeline que aplique los manifiestos (con `kubectl`) creados para la aplicacion web-go vista anteriormente
8. Crear un pipeline que en la rama develop construya la imagen y la publique y que en la rama master aplique el manifiesto
9. Crear un pipeline que actualice la imagen del deployment con la nueva imagen construida (esto se logra utilizando el `BUILD_NUMBER` del job de jenkins).
10. Crear un pipeline que en la rama develop contruya la imagen, la publique y luega tambien que despliegue el manifiesto en una namespace de desarrollo, y que en la rama master solo despliegue el manifiesto en el namespace de produccion (es posible que se necesite dos manifiestos)

### Recursos

- [Usar un Jenkinsfile](https://www.jenkins.io/doc/book/pipeline/jenkinsfile/)
- [Sintaxis](https://www.jenkins.io/doc/book/pipeline/syntax/)
- [Docker Pipeline plugin](https://docs.cloudbees.com/docs/admin-resources/latest/plugins/docker-workflow)
- [K8s Plugin](https://plugins.jenkins.io/kubernetes/)
- Variables de ambiente ${YOUR_JENKINS_HOST}/env-vars.html
