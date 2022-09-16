# Base de Datos en CI-CD

## **Ejercicio 1**
---

Realizar las siguientes actividades

1. Crear un container con una base de Datos MySQL
2. Crear un conjunto de scripts que realicen los siguiente (uno por archivo)
    1. Crear tablas
    2. Agregar columnas
    3. Eliminar columnas
    4. Borrar datos en una tabla
3. Validar que los scripts funcionen
4. Versionar los scripts para que puedan ser interpretados por [flyway](https://flywaydb.org/documentation/concepts/migrations.html#naming)
    1. Todas tienen que ser migraciones menos el script que borra datos, el cual tiene que ser repetible
3. Usar la imagen de [flyway](https://hub.docker.com/r/flyway/flyway) y aplicar los scripts en la base de datos.
4. Volver a ejecutar el mismo conjunto de scripts y validar los resultados.
5. Crear un nuevo script con numero de version anterior a los aplicados y validar su aplicacion.

## **Ejercicio 2**
---

En el entorno de Jenkins creado en Kubernetes

1. Crear un pod template que contenga el container de flyway
2. Crear un repositorio que contenga el siguiente [manifiesto](https://gist.githubusercontent.com/nelsonyaccuzzi/e99e931224f483b92ac93ddc1ed01907/raw/4b6154c1ffb84be4bea96a1f5242cb50863abe3c/mysql.yaml) para desplegar una base de datos MySQL
3. Agregar los scripts del ejercicio anterior al repositorio
4. Crear un pipeline que despliega la base de datos y ademas aplica con el container de flyway los scripts anteriores
5. Agregar un nuevo scripts en el repositorio y validar su aplicacion por el pipeline.

