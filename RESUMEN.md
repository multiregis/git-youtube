# Resumen operaciones

**inicia un repositorio**
git init 

**añade todos los ficheros al staging area**
git add . 

**añade todos los ficheros en el staging area al repositorio**
git commit -m "comentario"

**añade todos los ficheros modificados al staging area y al repositorio**
git commit -am "añade y commitea ficheros"

**modificar descripción del último commit**
git commit --amend 

**subir repositorio a github o similar**
git remote add origin https://github.com/etc/etc/repositorio.git

**subir / bajar cambios en el repositorio**
git push / pull 

**clonar un repositorio**
git clone https://github.com/etc/etc/repositorio.git

**marca una actualización con un tag**
git tag 15-09-20v1 -m "version 1 del proyecto"

**subir las tags al repositorio**
git push --tags

**crear una rama en el repositorio**
git branch nombreRama

**moverte a una rama concreta del repositorio**
git checkout nombreRama

**volver a la rama master**
git checkout master

**ver las ramas del proyecto**
git branch

**unir ramas (SIEMPRE se debe hacer desde la rama master)**
git merge nombreRama

**borrar una rama**
git branch -d nombreRama

**muestra el status de nuestros arhivos y directorios**
git status -s

**muestra instantáneas archivadas**
git log --oneline

**restaura a una instantánea concreta, donde XXXXX es el codigo de la instantánea; ojo que pierdes las instantáneas posteriores**
git reset --hard XXXXX

https://www.youtube.com/watch?v=iT4UOkyI09k
