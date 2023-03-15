# Curso de _Git_ & _GitHub_

https://jonmircha.com/git

https://www.youtube.com/watch?v=suzMNqDQiyU&t=13s&ab_channel=jonmircha


## Para repositorios nuevos

git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
Para repositorios existentes
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main

## Para reemplazar la rama master por main en GitHub

## Paso 1
### Crea la rama local main y pásale el historial de la rama master
git branch -m master main


## Paso 2
### Haz un push de la nueva rama local main en el repositorio remoto de GitHub
git push -u origin main


## Paso 3
### Cambia el HEAD actual a la rama main
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
## Paso 4
### Cambia la rama default de master a main en tu repositorio de GitHub. 

## Paso 5
### Elimina la rama master del repositorio remoto
git push origin --delete master

## Para reemplazar la rama master por main en Git
git config --global init.defaultBranch main


# Para sacar la ayuda

### Ayuda en la terminal
git "comando" -h
### Ayuda en el navegador
git help "comando"


# Ignorar archivos

En el archivo **.gitignore** incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con gitignore.io.

"# Esto es un comentario" (Dentro del archivo gitignore)
archivo.ext
carpeta
/archivo_desde_raiz.ext
### Ignorar todos los archivos que terminen en .log
*.log
### Excepto production.log
!production.log
### Ignorar los archivos terminados en .txt dentro de la carpeta doc,
### pero no en sus subcarpetas
doc/*.txt
### Ignorar todos los archivos terminados en .txt dentro de la carpeta doc
### y también en sus subcarpetas
doc/**/*.txt


# Clonar repositorios

### Siempre terminado en **.git**
git clone https://github.com/usuario/repositorio.git


# Manejo de ramas (branches)

### Crear rama
git branch nombre-rama

### Cambiar de rama
git checkout nombre-rama

### Crear una rama y cambiarte a ella
git checkout -b rama

### Eliminar rama
git branch -d nombre-rama

### Eliminar ramas remotas
git push origin --delete nombre-rama

#eliminar rama (forzado)
git branch -D nombre-rama

### Listar todas las ramas del repositorio
git branch

### Lista ramas no fusionadas a la rama actual
git branch --no-merged

### Lista ramas fusionadas a la rama actual
git branch --merged

### Rebasar ramas
git checkout rama-secundaria
git rebase rama-principal

### Si es la primera vez que hago un push a una rama nueva (crea la rama en el remoto y hace el push)
git push -u origin "nombre-rama"

### Borro la rama en el repositorio remoto
git push origin --delete "nombre-rama"

**Cuando creas una rama, la rama nueva toma como referencia el contendio desde la rama donde saltas**


# Fusiones
Une dos ramas. Para hacer una fusión necesitamos:

Situarnos en la rama que se quedará con el contenido fusionado.
Fusionar.
Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.
Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.

### Nos cambiamos a la rama principal que quedará de la fusión
git checkout rama-principal

### Ejecutamos el comando merge con la rama secundaria a fusionar
git merge rama-secundaria



# Cambios
Puedes agregar modificaciones al último cambio

## Sin editar el mensaje del último commit
git commit --amend --no-edit
{
    1- "Agrego el contenido que faltó"
    2- git commit --amend --no-edit
    3- git add .
    4- git commit --amend --no-edit (Aca ya estaria hecho, luego se puede hacer el push)
    5- git push  (opcional)
}

## Editando el mensaje del último commit
git commit --amend -m "nuevo mensaje para el último commit"

## Eliminar el último commit
git reset --hard HEAD~1

Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas , sin afectar el repositorio como tal.

## Cambiar a una rama
git checkout nombre-rama

## Cambiar a un commit en particular
git checkout id-commit



# Registro del historial

### git log nos permite conocer todo el historial de un proyecto, con la información de la fecha, el autor y id de cada cambio.
git log

### muestra en una sola línea por cambio
git log --oneline

### guarda el log en la ruta y archivo que especifiquemos
git log > commits.txt

### muestra el historial con el formato que indicamos
git log --pretty=format:"%h - %an, %ar : %s"

### cambiamos la n por cualquier número entero y mostrará los n cambios recientes
git log -n

### muestra los cambios realizados después de la fecha especificada
git log --after="2019-07-07 00:00:00"

### muestra los cambios realizados antes de la fecha especificada
git log --before="2019-07-08 00:00:00"

### muestra los cambios realizados en el rango de fecha especificado
git log --after="2019-07-07 00:00:00" --before="2019-07-08 00:00:00"

### muestra una gráfica del historial de cambios, rama y fusiones
git log --oneline --graph --all

### muestra todo el registro de acciones del log
### incluyendo inserciones, cambios, eliminaciones, fusiones, etc.
git reflog

### diferencias entre el Working Directory y el Staging Area
git diff



# Reseteo del historial
Podemos eliminar el historial de cambios del proyecto hacia adelante con respecto de un punto de referencia.

### Nos muestra el listado de archivos nuevos (untracked), borrados o editados
git status

### Borra HEAD
git reset --soft

### Borra HEAD y Staging
git reset --mixed

### Borra todo: HEAD, Staging y Working Directory
git reset --hard

### Deshace todos los cambios después del commit indicado, preservando los cambios localmente
git reset id-commit

### Desecha todo el historial y regresa al commit especificado
git reset --hard id-commit



# Resetear un repositorio

Si en algún momento tienes la necesidad de resetear el historial de cambios de un repositorio para que quede como si lo acabarás de crear ejecuta esta serie de comandos:

cd carpeta-repositorio
mv .git/config ~/saved_git_config
rm -rf .git
git init
git branch -M main
git add .
git commit -m "Commit inicial"
mv ~/saved_git_config .git/config
git push --force origin main

Cambio de prueba!!!

# Remotos
El remoto es la referencia que va a apuntar al repositorio en la nube  

### muestra los orígenes remotos del repositorio
git remote

### muestra los orígenes remotos con detalle
git remote -v

### agregar un orígen remoto
git remote add nombre-orígen https://github.com/usuario/repositorio.git

### renombrar un orígen remoto
git remote rename nombre-viejo nombre-nuevo

### eliminar un orígen remoto
git remote remove nombre-orígen

### descargar una rama remota a local diferente a la principal
git checkout --track -b rama-remota origin/rama-remota


<!-- Documentacion de versiones: https://semver.org/lang/es/ -->
# Etiquetas
Con esta opción git nos permite versionar nuestro código, librería o proyecto. (permite asignar un numero de version)

### listar etiquetas
git tag

### crea una etiqueta
git tag numero-versión

### eliminar una etiqueta
git tag -d numero-versión

### mostrar información de una etiqueta
git show numero-versión

### sincronizando la etiqueta del repositorio local al remoto
git add .
git  tag v1.0.0
git commit -m "v1.0.0"
git push origin numero-versión

### generando una etiqueta anotada (con mensaje de commit)
git add .
git tag -a "v1.0.0" -m "Mensaje de la etiqueta"
git push --tags



# GitHub Pages
gh-pages es una rama especial para crear un sitio web a tu proyecto alojado directamente en tu repositorio de GitHub.

URL del repositorio: https://github.com/usuario/repositorio
URL del sitio: https://usuario.github.io/repositorio
Para crear esta rama especial en GitHub ejecutamos los siguientes comandos:

git branch gh-pages
git checkout gh-pages

git remote add origin https://github.com/usuario/repositorio.git
git push origin gh-pages

### Para descargar los cambios del repositorio remoto al local
git pull origin gh-pages



# Colaboración en GitHub
Para poder colaborar en proyectos alojados en GitHub necesitamos hacer uso de los forks y pull requests, herramientas que nos ofrece la plataforma para dicho objetivo.

A continuación describo el proceso de colaboración en GitHub.

-Forkea el repositorio en el que quieras colaborar https://docs.github.com/en/get-started/quickstart/fork-a-repo
-Una vez forkeado el repositorio en tu cuenta de GitHub, clónalo en tu equipo de cómputo.
-En el repositorio local hay que configurar los orígenes remotos de tu nueva copía para tener ambos remotos, los originales (origin) y los de tu copia
-Crea una rama nueva en tu fork local para hacer tu colaboración, y sincrónizala con tu repositorio remoto
-Configura tu repositorio para que acepté cambios (pull requests)
-Crea una pull request, para hacerlo
-Espera a que el dueño del repositorio original, acepte tus cambios.
-Una vez que acepten tu pull request, es recomendable que borres la rama en la que trabajaste el cambio y actualices tu repositorio forkeado, con los cambios del repositorio original.
-Anexo un resumen de los comandos a ejecutar para colaborar en un repositorio de GitHub:

### forkear repositorio
git clone https://github.com/usuario/repositorio.git
git remote -v
git remote rename origin fork
git remote add origin https://github.com/usuario/repositorio.git
git checkout -b rama-nueva
git push fork rama-nueva

### solicitar el pull request
### aceptar el pull request
git checkout main
git pull origin main
git push fork main
git branch -d rama-nueva
git push fork --delete rama-nueva













