# hello-world

##Tutoriales

Inicial
>https://guides.github.com/activities/hello-world/

Duplicar Repositorio
>https://help.github.com/articles/duplicating-a-repository/


##Comandos
https://www.youtube.com/playlist?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-

###Commit

Ver estado del repositorio
>git status

agregar archivos al area de 'staging' (nuevos o modificados)
>git add index.html

commitear
>git commit -m "mensaje descriptivo"


###Diff

Ver que cambios se hicieron a los archivos (diferencia entre la working copy y stage area)
>git diff

Diferencia entre staging area y commit mas reciente
>git diff --staged

Al cambiar un archivo en stage, al ejecuar
>git status
muestra datos en stage y no stage

Para comparar tooodos los cambios realizados con el ultimo commit (head commit)
>git diff HEAD

Filtrar por color solo las palabras cambiadas
>git diff --color-words
>git diff --word-diff

Muestra solo los cambios en archivos sin el resto de informacion
>git diff -stat

###LOG
Mostrar el historial

Listar cambios en forma cronologica, contiene:
- id (exadecimal)
- autor
- fecha

>git log

Te muestra un resumen (parte_id mensaje)
>git log --oneline

ver el log + archivos que se modificaron
>git log --stat

Ver el contenido que cambio entre commits
>git log --patch

combina ambas opciones
>git log --patch --oneline

Graficar o ve una representacion ascci de todos los commits
>git log --graph --all --decorate --oneline


###Remove

Elimina el archivo del sistema de archivos, y lo marca como elimado en la stage area
cuando se commitea se elimina de futuras revisiones.
>git rm filename.txt

Si se elimina un archivo directamente
>rm filename.txt

al hacer git status se muestra que se elimino, pero no se encuentra el cambio en la stage area, para que se elimine utilizar el comando normal, para que se agregue la eliminacion al stage area
>git rm filename.txt
---
Para elminar muchos archivos externamente, se pueden agregar a eliminar en el stage con:
>git add -u .

Si quieres eliminar un archivo del repositorio, pero dejarlo en tu carpeta usar:
>git rm --cached filename.txt

Se agrega al stage para eliminar y git lo deja de ratrear (track)
---

###Move files

Cambiar de nombre y mover archivos es lo mismo

Mueve los archivos y git lo registra como cambio de nombre
>git mv original.txt ubicacionNueva/original.txt

Si se mueve el archivo por sistema operativo
>mv original.txt ubicacionNueva/original.txt

git lo registra como que existe un nuevo archivo (ubicacionNueva/original.txt) y que otro se elimino (original.txt)
Para arreglar eso y se registre como que se movio hacer:
>git rm original.txt
>git add ubicacionNueva/original.txt
---

Si se mueven varios archivos por sistema operativo se puede agragar los cambios a la staging area utilizando:
>git add -A .

Para ver el log de un archivo
>git log --stat -- ubicacionNueva/original.txt
Pero no muestra el historia antes de moverlo

