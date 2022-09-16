# CI-CD

## **Ejercicio 1**
---

1. Desplegar Jenkins en K8s
2. Conectar Jenkins con K8s
3. Instalar los plugins de docker y K8s
4. Crear un Pod Template con el container Docker
5. Crear un Pipeline (a partir de un Jenkinsfile) que compile el dockerfile del siguiente proyecto https://github.com/nelsonyaccuzzi/web-go-public
6. Crear un container que tenga solo el binario de kubectl, pushearlo a dockerhub
7. Agregar el container al pod template que anteriormente creamos
8. Crear un pipeline que haga un `kubectl get pod` del cluster actual (es necesario pasar los parametros `-s` `--token` `--insecure-skip-tls-verify` con sus respectivos valores)
9. Crear un pipeline que cuando se ejecute en la rama develop haga el build de una imagen de docker anterior, y cuando este en la rama master haga un `kubectl get pod` del cluster
10. Crear un pipeline que cuando se ejecute en la rama develop haga el build de la imagen docker y lo pushee a dockerhub
11. Crear un pipeline que aplique los manifiestos (con `kubectl`) creados para la aplicacion web-go vista anteriormente
12. Crear un pipeline que en la rama develop construya la imagen y la publique y que en la rama master aplique el manifiesto
13. Crear un pipeline que actualice la imagen del deployment con la nueva imagen construida (esto se logra utilizando el `BUILD_NUMBER` del job de jenkins).
14. Crear un pipeline que en la rama develop contruya la imagen, la publique y luega tambien que despliegue el manifiesto en una namespace de desarrollo, y que en la rama master solo despliegue el manifiesto en el namespace de produccion (es posible que se necesite dos manifiestos)

### Recursos

- [Usar un Jenkinsfile](https://www.jenkins.io/doc/book/pipeline/jenkinsfile/)
- [Sintaxis](https://www.jenkins.io/doc/book/pipeline/syntax/)
- [Docker Pipeline plugin](https://docs.cloudbees.com/docs/admin-resources/latest/plugins/docker-workflow)
- [K8s Plugin](https://plugins.jenkins.io/kubernetes/)
- Variables de ambiente ${YOUR_JENKINS_HOST}/env-vars.html

## **Ejercicio 2**
---

1. Tomar como base el siguiente [repositorio](https://github.com/nelsonyaccuzzi/web-go-public)
2. Ingresar a [Travis](https://app.travis-ci.com/) y loguearse con la cuenta de GitHub propia, brindar los permisos necesarios.
3. Leer los recursos provistos
4. Modificar el codigo para que imprima tu nombre, el año, el nombre de la catedra y tambien el link al repositorio.
5. Crear un archivo `.travis.yml` en el repo y crear un pipeline que compile la imagen de docker
6. Modificar el pipeline para que pushee la imagen a un repo en DockerHub
7. Modificar el pipeline para que
	1. Si la rama no es main, compile la imagen
	2. Si la rama es main, compile la imagen y la pushee a un repo en Dockerhub
8. Modificar el pipeline para que cuando la rama es main ademas despliegue la imagen en un servidor brindado por el profesor.
    1. Conectarse al servidor por clave SSH plana en el repositorio
    2. Encriptar la clave con alguna herramienta y desencriptarla en el CI.
9. Agregar un badge del build en un readme dentro del repositorio


### Recursos

- [Conceptos Basicos](https://docs.travis-ci.com/user/for-beginners/)
- [Job Lifecycle](https://docs.travis-ci.com/user/job-lifecycle/)
- [Stages](https://docs.travis-ci.com/user/build-stages/)
- [Badge](https://shields.io/category/build )