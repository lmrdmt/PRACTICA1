# SRI


## 1. Descargar y comprobar una imagen en tu equipo

Para descargar una imagen de **Ubuntu** en Docker, usa el siguiente comando:

docker pull ubuntu


Luego, para verificar que la imagen ha sido descargada correctamente:

docker images

Este comando mostrará una lista de las imágenes disponibles en tu equipo, incluyendo **Ubuntu**.

---

## 2. Crear un contenedor sin nombre

Crea un contenedor sin especificar un nombre explícito con:

docker run -d ubuntu

### ¿El contenedor queda arrancado?

Sí, el contenedor se ejecuta en segundo plano en modo **detached** gracias al parámetro `-d`.

### ¿Cómo obtener el nombre del contenedor?

Para obtener el nombre o el ID del contenedor, ejecuta:

docker ps

Esto te mostrará los contenedores activos junto con su **ID**, **nombre** y otros detalles.

---

## 3. Crear un contenedor con el nombre 'u1' y acceder a él

Para crear un contenedor con el nombre **u1**, ejecuta:

docker run -d --name u1 ubuntu


### ¿Cómo accedo al contenedor 'u1'?

Usa el siguiente comando para acceder a la terminal de **bash** del contenedor:

docker exec -it u1 bash

Esto abrirá una sesión interactiva dentro del contenedor.

---

## 4. Comprobar la IP del contenedor y hacer ping a Google

Dentro del contenedor, puedes comprobar su dirección IP ejecutando:

ip a

Luego, para hacer ping a **Google**, utiliza:

ping google.com

---

## 5. Crear un contenedor con el nombre 'bono' y hacer ping entre contenedores

Crea un segundo contenedor llamado **bono** con:

docker run -d --name bono ubuntu


### ¿Se puede hacer ping entre los contenedores?

Para que dos contenedores se comuniquen entre sí, deben estar en la misma red personalizada. Primero, crea una red:

docker network create mi_propia_red

Luego, conecta ambos contenedores a esta red:

docker network connect mi_propia_red u1
docker network connect mi_propia_red bono


Para hacer ping entre los contenedores, accede a **u1** y ejecuta:

docker exec -it u1 ping bono

---

## 6. ¿Qué pasa si cierras las terminales?

Si cierras la terminal, los contenedores creados en modo **detached** (`-d`) seguirán ejecutándose en segundo plano. Puedes verificarlo con:

docker ps

---

## 7. ¿Cuánta memoria en disco duro has ocupado?

Para comprobar el espacio en disco que ocupan las imágenes y contenedores de Docker, ejecuta:

docker system df

Esto te mostrará un desglose del espacio utilizado por imágenes, contenedores, volúmenes y redes.

---

## 8. ¿Cuánta RAM ocupan los contenedores?

Para ver el consumo de memoria RAM de los contenedores, crea varios contenedores adicionales:

docker run -d --name calisto ubuntu
docker run -d --name listo ubuntu

Luego, para visualizar el uso de RAM y otros recursos:

docker stats

---

## 9. ¿Cómo clonaste el repositorio?
Para crear un repositorio local, deberemos tener un token clasic activado.
Cuando nos pide una contraseña al clonar deberemos utilizar el código del token.
El repositorio de GitHub fue clonado usando el siguiente comando:

git clone https://github.com/lmrdmt/SRI.git

---

## 10. ¿Cómo agregar el archivo `readme2.md`?

Primero, crea el archivo `readme2.md` en tu entorno local:

touch readme2.md

Luego, añade el siguiente contenido al archivo:

echo "Esta es una práctica de Docker para la gestión de contenedores." > readme2.md

---

## 11. ¿Cómo subir los archivos editados y el archivo `readme2.md`?

Añade y sube los archivos modificados al repositorio remoto en **GitHub**:
Estos comandos deben realizarse dentro del directorio remoto (ejemplo SRI/)
git add README.md
git commit README.md
git push 

---

## 12. ¿Cómo comprobar que existen diferencias entre tu repositorio local y el remoto?

Para verificar si hay diferencias entre el repositorio local y el remoto, primero obtén las últimas actualizaciones del repositorio remoto con:

git fetch

Luego, usa el siguiente comando para comparar las diferencias:

git diff origin/main

---

## Conclusión

Este documento detalla los pasos necesarios para gestionar contenedores en Docker, acceder a ellos, comprobar el uso de recursos, y trabajar con un repositorio en GitHub utilizando **Git**.
```

