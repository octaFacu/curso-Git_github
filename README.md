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

### esto es un comentario (Dentro del archivo gitignore)
archivo.ext
carpeta
/archivo_desde_raiz.ext
### ignorar todos los archivos que terminen en .log
*.log
### excepto production.log
!production.log
### ignorar los archivos terminados en .txt dentro de la carpeta doc,
### pero no en sus subcarpetas
doc/*.txt
### ignorar todos los archivos terminados en .txt dentro de la carpeta doc
### y también en sus subcarpetas
doc/**/*.txt
