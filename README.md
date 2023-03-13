# Curso de _Git_ & _GitHub_

https://jonmircha.com/git

https://www.youtube.com/watch?v=suzMNqDQiyU&t=13s&ab_channel=jonmircha




## Para sacar la ayuda

### Ayuda en la terminal
git "comando" -h
### Ayuda en el navegador
git help "comando"


## Ignorar archivos

En el archivo **.gitignore** incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con gitignore.io.

### Rsto es un comentario (Dentro del archivo gitignore)
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


## Clonar repositorios

### Siempre terminado en **.git**
git clone https://github.com/usuario/repositorio.git


## Manejo de ramas (branches)

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


## Fusiones
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



### Cambios
Puedes agregar modificaciones al último cambio

## Sin editar el mensaje del último commit
git commit --amend --no-edit

## Editando el mensaje del último commit
git commit --amend -m "nuevo mensaje para el último commit"

## Eliminar el último commit
git reset --hard HEAD~1

Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas , sin afectar el repositorio como tal.

## Cambiar a una rama
git checkout nombre-rama

## Cambiar a un commit en particular
git checkout id-commit