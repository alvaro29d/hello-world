# hello-world

##Tutoriales

Inicial
>https://guides.github.com/activities/hello-world/

Duplicar Repositorio
>https://help.github.com/articles/duplicating-a-repository/


##GitHub & Git Foundations • Training
https://www.youtube.com/playlist?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-

###Config Git

Config usuario y e-mail
>git config --global user.name
>git config --global user.mail

Normalizar final de Lineas
>git config --global core.autocrlf true

Config colores
>git config --global color.ui auto

Scopes Leves
- system (menor prioridad)
- global
- local (mayor prioridad)

###Iniciar repositorio

Crear un repositorio en un proyecto existente no versionado
>git init

Antes de comenzar el proyecto se puede crear el repositorio:
>git init nombreNuevoDirectorio

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
>git diff --stat

###LOG
Mostrar el historial

Listar cambios en forma cronologica, contiene:
- id (exadecimal)
- autor
- fecha

>git log

---

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

---

Si se elimina un archivo directamente
>rm filename.txt

---

al hacer git status se muestra que se elimino, pero no se encuentra el cambio en la stage area, para que se elimine utilizar el comando normal, para que se agregue la eliminacion al stage area
>git rm filename.txt

---

Para elminar muchos archivos externamente, se pueden agregar a eliminar en el stage con:
>git add -u .

---

Si quieres eliminar un archivo del repositorio, pero dejarlo en tu carpeta usar:
>git rm --cached filename.txt

Se agrega al stage para eliminar y git lo deja de ratrear (track)


###Move files

Cambiar de nombre y mover archivos es lo mismo

Mueve los archivos y git lo registra como cambio de nombre
>git mv original.txt ubicacionNueva/original.txt

---

Si se mueve el archivo por sistema operativo
>mv original.txt ubicacionNueva/original.txt

---

git lo registra como que existe un nuevo archivo (ubicacionNueva/original.txt) y que otro se elimino (original.txt)
Para arreglar eso y se registre como que se movio hacer:
>git rm original.txt
>git add ubicacionNueva/original.txt

---

Si se mueven varios archivos por sistema operativo se puede agragar los cambios a la staging area utilizando:
>git add -A .

---

Para ver el log de un archivo
>git log --stat -- ubicacionNueva/original.txt

Pero no muestra el historia antes de moverlo, para que lo haga:
>git log --stat -M --follow -- ubicacionNueva/original.txt

---

Git considera un movimiento cuando encuentra dos archivos similares que se hayan agregado y eliminado. De forma predeterminada git considera que son iguales cuando son 50% iguales, ese umbral se lo puede ajustar (similarity).

Video the 'Ship of Theseus'
tipos de cambios
cbs break history

###Ignore
Evitar comitear o agragar al area de stage archivos

Crear un archivo .gitignore agregarlo al stage y commitearlo
>touch .gitignore
>git add .gitignore
>git commit -M "agregando archivos a ignorar"

El archivo debe contener los nombres o patrones de archivos a ignorar

- nombre de archivo: fileName.txt
- patron: *.log
- ignorar direcotrio: nombreDirectorio/

---

Se puede agregar archivos .gitignore a subdirectorios, estos tomaran precedencia, y permiten negar patrones agregando:
>!nombreDeArchivo

---
Usar # para comentarios


---

Para listar todos los archivos ignorados:
>git ls-files --others --ignores --exclude-standard

###Branch

Master representa lo que esta en produccion.
Para trabajar en un repositorio crear una branch.
>git branch nombreBranch

eliminar branch
>git branch -d nombreBranch

si los cambios no estan completamente aplicados al master sale un mensaje de error, utilizar -D para forzar la eliminacion

---

Para moverse entre branches usar
>git checkout nombreBranchDestino

Cualquier cambio que este en el staging area permanecera ahi, y se podra sobreescribir


###Checkout

Para ver en que branch estamos se utilizan:
>git branch
>git status

---
Para cambiar de branch
>git checkout nombreBranch

Para cambiar a puntos del historial (log_id) detachHead no se puede hacer commits
>git checkout log_id

---

Para revertir cambios se usa:
>git checkout -- nombreArchivoARevertir.txt

---

Crear branch y moverse a esa nueva branch
>git checkout -b nombreNuevaBranch


###Merge

Ir a repositorio master donde queremos importar los cambios de un branch y usar merge
>git checkout master
>git merge branchConCambios

---

Tratar de hacer merge y si hay conflictos buscalos con 
>git merge branchConCambios
>git status

Editar los archivos con conflictos en un editor
Identificar Head como repositorio master
Agregar los cambios al staging area
Commit cambios
>git add nombreArchivoConConflictos
>git commit

---

Limpia el working directory y stage area con el ultimo commit 
>git merge --abort

---

Para commitear una branch pisando los cambios del head
>git merge --squash branchConCambios
>git commit -m "importar tooodos los cambios"

---

eliminar el branch ya importado
>git branch -d nombreBranchYaImportada

###Network

Si tenemos un repositorio que solo se encuentra en la laptop, hay que confgurar donde se enviara la informacion
>git remote add origin http://github.com/alvaro29d/hello-world
>git remote add nameDestination URLDestination

para modificar la url:
>git remote set-url origin http://github.com/nueva/url

para eliminar uno de los 'remote'
>git remote rm origin

para consultar las urls:
>git remote -v

Consultar branch de la localizacion remote
>git branch -r

###Fetch Pull Push

Fetch trae la informacion del repo remoto y la coloca en nuestro branch remote (git branch -r)
>git fetch origin

Pull llama primero Fetch y luego a Merge, Ej: git traera todos los cambios del branch desde el repo remoto
>git checkout nombreBranch
>git pull origin

Push envia los cambios al repo remoto y tambien actualiza el arbol de trakeo de branches
>git push origin


###Graphic UI

Github Desktop es una aplicacion con soporte para Windows y Mac, Linux Jodete

