# Notas del libro ProGit

mostrar/cambiar la configuracion (global, de un repositorio, etc)
`git config`

página del manual
`git help config`
`git config --help`

listar configuración
`git config --list`

configuracion global o local (del repositorio actual; local por defecto)
`git config [--global|--local]`

mostar un parámetro concreto de la configuración
`git config user.name`

iniciar repositorio 
`git init`

añadir ficheros al repositorio
`git add [*|fichero]`

confirmar cambios pendientes
`git commit`
`git commit -m "primera version"`

mostrar estado del repositorio
muestra ficheros con seguimiento y sin seguimiento
`git status`

muestra estado resumido
`git statut -s`

fichero para ignorar cambios
`.gitignore`
algunas reglas para el fichero .gitignore
<pre>
# ignora los archivos terminados en .a
*.a
# pero no lib.a, aun cuando había ignorado los archivos terminados en .a en la línea
anterior
!lib.a
# ignora unicamente el archivo TODO de la raiz, no subdir/TODO
/TODO
# ignora todos los archivos del directorio build/
build/
# ignora doc/notes.txt, pero no este: doc/server/arch.txt
doc/*.txt
# ignora todos los archivos .txt del directorio doc/
doc/**/*.txt
</pre>

ver los cambios (preparados y sin preparar)
`git diff [--staged]`

ver el historial de confirmaciones, ejemplos
normal
`git log`

opciones típicas de git log

| parámetro        | descripción                                                                                                                                                                    |     |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- |
| -p               | Muestra el parche introducido en cada confirmación.                                                                                                                            |     |
| --stat           | Muestra estadísticas sobre los archivos modificados en cada confirmación.                                                                                                      |     |
| --shortstat o -s | Muestra solamente la línea de resumen de la opción --stat.                                                                                                                     |     |
| --name-only      | Muestra la lista de archivos afectados.                                                                                                                                        |     |
| --name-status    | Muestra la lista de archivos afectados, indicando además si fueron añadidos, modificados o eliminados.                                                                         |     |
| --abbrev-commit  | Muestra solamente los primeros caracteres de la suma SHA-1, en vez de los 40 caracteres de que se compone.                                                                     |     |
| --relative-date  | Muestra la fecha en formato relativo (por ejemplo, “2 weeks ago” (“hace 2 semanas”)) en lugar del formato completo.                                                            |     |
| --graph          | Muestra un gráfico ASCII con la historia de ramificaciones y uniones.                                                                                                          |     |
| --pretty         | Muestra las confirmaciones usando un formato alternativo. Posibles opciones son oneline, short, full, fuller y format (mediante el cual puedes especificar tu propio formato). |     |

log resumido
`git log -s`

log con formato específico
`git log --pretty=format:"%h - %an, %ar : %s"`

opciones útiles de pretty=format

| Opción | Descripción de la salida                               | 
| ------ | ------------------------------------------------------ |
| %H     | Hash de la confirmación                                |
| %h     | Hash de la confirmación abreviado                      |
| %T     | Hash del árbol                                         |
| %t     | Hash del árbol abreviado                               |
| %P     | Hashes de las confirmaciones padre                     |
| %p     | de las confirmaciones padre abreviados                 |
| %an    | Nombre del autor                                       |
| %ae    | Dirección de correo del autor                          |
| %ad    | Fecha de autoría (el formato respeta la opción -–date) |
| %ar    | Fecha de autoría, relativa                             |
| %cn    | Nombre del confirmador                                 |
| %ce    | de correo del confirmador                              |
| %cd    | Fecha de confirmación                                  |
| %cr    | de confirmación, relativa                              |
| %s     | Asunto                                                 |

opciones para limitar la salida de git log

| Opción            | Descripción                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------- |
| -(n)              | Muestra solamente las últimas n confirmaciones                                                                |
| --since, --after  | Muestra aquellas confirmaciones hechas después de la fecha especificada.                                      |
| --until, --before | Muestra aquellas confirmaciones hechas antes de la fecha especificada.                                        |
| --author          | Muestra sólo aquellas confirmaciones cuyo autor coincide con la cadena especificada.                          |
| --committer       | Muestra sólo aquellas confirmaciones cuyo confirmador coincide con la cadena especificada.                    |
| -S                | Muestra sólo aquellas confirmaciones que añaden o eliminen código que corresponda con la cadena especificada. |

deshacer confirmaciones
`git commit --amend`

revertir archivos
`git reset HEAD CONTRIBUTING.md`

muestra las ramas activas
`git branch`

muestra la última confirmación
`git branch -v`

crear rama testing
`git branch testing`

ver dónde apunta cada rama
`git log`
`git log --oneline --decorate`

cambiar de rama (a la rama testing)
`git checkout testing`

cambiar de rama creándola al mismo tiempo
(crea la rama iss53)
`git checkout -b iss53`
creando la rama hotfix
`git checkout -b hotfix`
lo anterior es lo mismo que
`git branch iss53`
`git checkout iss53`

fusionar ramas (primero nos situamos en el destino)
`git checkout master`
e indicamos la rama a mergear (hotfix en este caso)
`git merge hotfix`

borrar la rama mergeada con éxito (hotfix en este caso)
`git branch -d hotfix`

muestra conflictos de fusion
`git status`

muestra herramienta (configurada) para la resolución de conflictos de fusión
`git mergetool`

muestra todas las ramas con trabajos sin fusionar
`git branch --no-merged`

ramas remotas, formato
`(remoto) / (rama)`
por ejemplo
`origin/master`
`bitbucket/develop`

sincronizar tu trabajo local con rama remota
`git fetch origin`
trae los cambios pero NO los fuiona con tu local

publicar tu trabajo local en rama remota
`git push origin serverfix`

guardar la contraseña en una caché temporal (para no tener que escribirla todo el tiempo)
`git config --global credential.helper cache`

listar ramas locales con info extendida
`git branch -vv`

traer y fusionar ramas remotas con la local (hace fecth y merge)
`git pull origin`
trae los cambios Y los fusiona automáticamente

eliminar ramas remotas (==ojo==)
`git push origin --delete serverfix`

`git rebase` permite reorganizar ramas locales o remotas, pero es peligroso y ==NUNCA SE DEBE UTILIZAR CON RAMAS REMOTAS (enviadas, push)== por lo que me lo voy a saltar, ya que no es imprescindible. se utiliza para reorganizar ramas locales ==ANTES== de enviarlas a repos remotos

