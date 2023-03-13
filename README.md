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

### Si es la primera vez que hago un push a una rama nueva (la crea en el remoto y hace el push)
git push -u origin "nombre-de-la-rama"


**Cuando creas una rama, la rama nueva toma como referencia el contendio desde la rama donde saltas**



