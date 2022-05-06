# Metodología: Documentación del proceso para la creación del repositorio y la estructura web

## Creación de un nuevo Repositorio
Comenzamos en nuestro perfil de **GitHub**, donde he creado un nuevo repositorio y sitúo en **Pontedatos** con mi nombre sin espacios ni tildes. Así he generado la dirección que me permitiría trabajar con la terminal: `github.com/Pontedatos/gabriela-junquera`.

## Pasos desde la terminal
Para poder editarlo desde mi terminal, he ejecutado el comando `git clone` y he clonado el repositorio en una carpeta nueva (creada a partir de `mkdir`) para así no crear confusión con otras carpetas de la asignatura en el curso. Sin embargo, en este repositorio/carpeta solo hay un README.md que lógicamente está vacío, y me dispongo a copiar el resto de las prácticas del curso desde mi repositorio personal al nuevo de Pontedatos. Para ello, ejecuto el comando `cp` y la dirección del archivo que quiero copiar (origen), y después la dirección de la carpeta donde quieres copiar el archivo (destino). 

Es importante recordar que, antes de recopilar las prácticas en la carpeta nueva, es necesario borrar el README.md de antes para sustituirlo con el README.md de mi repositorio personal. Para ello, usamos el comando `rn` (rm README.md).
Una vez tenía todo preparado he ejecutado los siguientes comandos para subir los documentos de mi nueva carpeta con las prácticas anterioresa mi repositorio de **GitHub**, corregidas previamente en el editor de texto: 

- `git add .` 
- `git commit -m "..."`
- `git status`
- `git push`
	- User
	- Token

Por último he comprobado que todo estaba correcto y que los cambios se habían volcado en `pontedatos/gabriela-junquera`. 

## Estructura Web en Pages
Una vez comprobado en **GitHub** que mi repositorio estaba creado y completo, me dispuse s crear la estructura para la web. Para ello, en la pestaña de Settings de mi repositorio activo Pages de GitHub, que me permitirá crear una página web.
El archivo README.md actuará como índice del repositorio y de su consiguiente página web, es decir, es el index.html. Por ello es necesario enlazar el resto de prácticas en el README, y que así sean accesibles en la página web. Edito, pues, el README desde la terminal mediante ``nano`` empleando lenguaje markdown. Actualizo y compruebo que los cambios se han guardado con éxito en GitHub.
