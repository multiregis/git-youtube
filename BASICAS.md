# Órdenes básicas

Extracto de Wikipedia
https://es.wikipedia.org/wiki/Git


Git ciclo de vida de archivos git

-   `git init`:

Esto crea un subdirectorio nuevo llamado .git, el cual contiene todos los archivos necesarios del repositorio – un esqueleto de un repositorio de Git. Todavía no hay nada en tu proyecto que esté bajo seguimiento.

-   `git fetch`:

Descarga los cambios realizados en el repositorio remoto.

-   `git merge _<nombre_rama>_`:

Impacta en la rama en la que te encuentras parado, los cambios realizados en la rama “nombre_rama”.

-   `git pull`:

Unifica los comandos _fetch_ y _merge_ en un único comando.

-   `git commit -m "<mensaje>"`:

Confirma los cambios realizados. El “mensaje” generalmente se usa para asociar al _commit_ una breve descripción de los cambios realizados.

-   `git push origin _<nombre_rama>_`:

Sube la rama “nombre_rama” al servidor remoto.

-   `git status`:

Muestra el estado actual de la rama, como los cambios que hay sin commitear.

-   `git add _<nombre_archivo>_`:

Comienza a trackear el archivo “nombre_archivo”.

-   `git checkout -b _<nombre_rama_nueva>_`:

Crea una rama a partir de la que te encuentres parado con el nombre “nombre_rama_nueva”, y luego salta sobre la rama nueva, por lo que quedas parado en esta última.

-   `git checkout -t origin/_<nombre_rama>_`:

Si existe una rama remota de nombre “nombre_rama”, al ejecutar este comando se crea una rama local con el nombre “nombre_rama” para hacer un seguimiento de la rama remota con el mismo nombre.

-   `git branch`:

Lista todas las ramas locales.

-   `git branch -a`:

Lista todas las ramas locales y remotas.

-   `git branch -d _<nombre_rama>_`:

Elimina la rama local con el nombre “nombre_rama”.

-   `git push origin _<nombre_rama>_`:

Commitea los cambios desde el branch local origin al branch “nombre_rama”.

-   `git remote prune origin`:

Actualiza tu repositorio remoto en caso que algún otro desarrollador haya eliminado alguna rama remota.

-   `git reset --hard HEAD`:

Elimina los cambios realizados que aún no se hayan hecho _commit_.

-   `git revert _<hash_commit>_`:

Revierte el _commit_ realizado, identificado por el “hash_commit”.

## Flujo de trabajo

Git plantea una gran libertad en la forma de trabajar en torno a un proyecto. Sin embargo, para coordinar el trabajo de un grupo de personas en torno a un proyecto es necesario acordar como se va a trabajar con Git. A estos acuerdos se les llama **flujo de trabajo**.[9](https://es.wikipedia.org/wiki/Git#cite_note-yukei-9)​ Un flujo de trabajo de Git es una fórmula o una recomendación acerca del uso de Git para realizar trabajo de forma uniforme y productiva.[10](https://es.wikipedia.org/wiki/Git#cite_note-10)​Los flujos de trabajo más populares son git-flow, GitHub-flow, GitLab Flow y One Flow.[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​

### Git-Flow

Creado en 2010 por Vincent Driessen.[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​ Es el flujo de trabajo más conocido. Está pensado para aquellos proyectos que tienen entregables y ciclos de desarrollo bien definidos.[9](https://es.wikipedia.org/wiki/Git#cite_note-yukei-9)​Está basado en dos grandes ramas con infinito tiempo de vida (ramas master y develop) y varias ramas de apoyo, unas orientadas al desarrollo de nuevas funcionalidades (ramas feature-*), otras al arreglo de errores (hotfix-*) y otras orientadas a la preparación de nuevas versiones de producción (ramas release-*). La herramienta gitflow [[1]](https://github.com/nvie/gitflow) facilita la automatización de las tareas implicadas en este flujo de trabajo[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​

#### _Master_

Es la rama principal. Contiene el repositorio que se encuentra publicado en producción, por lo que debe estar siempre estable.

#### _Development_

Es una rama sacada de _Master_. Es la rama de integración, todas las nuevas funcionalidades se deben integrar en esta rama. Luego que se realice la integración y se corrijan los errores (en caso de haber alguno), es decir que la rama se encuentre estable, se puede hacer un merge de development sobre la rama _Master_.

#### _Features_

Cada nueva funcionalidad se debe realizar en una rama nueva, específica para esa funcionalidad. Estas se deben sacar de _Development_. Una vez que la funcionalidad esté desarrollada, se hace un merge de la rama sobre _Development_, donde se integrará con las demás funcionalidades.

#### _Hotfix_

Son [errores de software](https://es.wikipedia.org/wiki/Error_de_software "Error de software") que surgen en producción, por lo que se deben arreglar y publicar de forma urgente. Es por ello, que son ramas sacadas de _Master_. Una vez corregido el error, se debe hacer una unificación de la rama sobre _Master_. Al final, para que no quede desactualizada, se debe realizar la unificación de _Master_ sobre _Development_.

#### _Release_

Las ramas de release apoyan la preparación de nuevas versiones de producción. Para ellos se arreglan muchos errores menores y se preparan adecuadamente los metadatos. Se suelen originar de la rama develop y deben fusionarse en las ramas master y develop.[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​

### GitHub-Flow

Creado en 2011 por GitHub[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​ y es la forma de trabajo sugerida por las funcionalidades propias de GitHub . Está centrado en un modelo de desarrollo iterativo y de despliegue constante. Está basado en cuatro principios:[9](https://es.wikipedia.org/wiki/Git#cite_note-yukei-9)​[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​

-   Todo lo que está en la rama master está listo para ser puesto en producción
-   Para trabajar en algo nuevo, debes crear una nueva rama a partir de la rama master con un nombre descriptivo. El trabajo se irá integrando sobre esa rama en local y regularmente también a esa rama en el servidor
-   Cuando se necesite ayuda o información o cuando creemos que la rama está lista para integrarla en la rama master, se debe abrir una pull request (solicitud de integración de cambios).
-   Alguien debe revisar y visar los cambios para fusionarlos con la rama master
-   Los cambios integrados se pueden poner en producción.

GitHub intenta simplificar la gestión de ramas, trabajando directamente sobre la rama master y generando integrando las distintas features directamente a esta rama[12](https://es.wikipedia.org/wiki/Git#cite_note-12)​

### GitLab Flow

Creado en 2014 por Gitlab.[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​Es una especie de extensión de GitHub Flow acompañado de un conjunto de pautas y mejores prácticas que apuntan a estandarizar aún más el proceso. Al igual que GitHub Flow propone el uso de ramas de funcionalidad (feature) que se originan a partir de la rama master y que al finalizarse se mezclan con la rama master. Además introduce otros tres tipos de ramas:[13](https://es.wikipedia.org/wiki/Git#cite_note-13)​

-   Ramas de entorno. Por ejemplo pre-production production. Se crean a partir de la rama master cuando estamos listos para implementar nuestra aplicación. Si hay un error crítico lo podemos arreglar en un rama y luego mezclarla en la rama de entorno.
-   Ramas de versión. Por ejemplo 1.5-stable 1.6-stable. El flujo puede incluir ramas de versión en caso de que el software requiera lanzamientos frecuentes.

### One Flow

Creado en 2015 por Adam Ruka. En él cada nueva versión de producción está basada en la versión previa de producción. La mayor diferencia entre One Flow y Git Flow es que One Flow no tiene rama de desarrollo.[11](https://es.wikipedia.org/wiki/Git#cite_note-patrickp-11)​
