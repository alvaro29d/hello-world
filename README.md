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
