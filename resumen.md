# Resumen de los contenidos de la asignatura

**Gabriela Junquera**

### Este documento consiste en documentar lo que hemos ido aprendiendo en la asignatura y lo evaluado en la parte práctica de la asignatura de Periodismo de Datos a lo largo del cuatrimestre. Se describirá cómo instalar y configurar el programa de emulación de la terminal pertinente, cómo usar `git` como nuestro software de control de versiones y, de ahí, cómo vincular nuestros repositorios locales con los que están subidos a GitHub.

## 1. Instalación de un programa de emulación de la terminal

Para empezar con la materia, las estudiantes que usamos Windows tuvimos que instalar y configurar dos programas diferentes de emulación de la terminal en nuestros ordenadores personales. Las alumnas que usan Apple trabajaron con XCode. 

**WSL** (*[Windows Subsystem for Linux](https://docs.microsoft.com/es-es/windows/wsl/)*), es una herramienta nativa de Microsoft Windows, que es una suerte de virtualización de una distribución de Linux, y en nuestro caso la hemos utilizado en combinación con Ubuntu. Hemos accedido a Ubuntu en su versión `cli`  a través de nuestra terminal. 

Por otro lado, instalamos también **[Cygwin](https://www.cygwin.com/)**, un programa que simula los sistemas Unix dentro de nuestro sistema operativo. Con **WSL** estábamos instalando un sistema operativo, pero con **Ubuntu** solo estaríamos instalando una terminal Unix. 

### WSL: instalación de Ubuntu

En el caso de WSL, su instalación la llevamos a cabo a través de la *PowerShell de Windows*, es decir, la terminal desarrollada por Microsoft. Para ello, abrimos nueva sesión de la terminal como administradores (ya que si no nos llevará a error si intentamos ejecutar casi cualquier comando), y ejecutar el comando `wsl --install -d Ubuntu`. Así especificamos que queremos instalar (`--install`) la distribución (`-d`) [Ubuntu](https://ubuntu.com/). 

Una vez se ha instalado, Windows nos pedirá que reiniciemos nuestro ordenador. Una vez hecho esto podremos ejecutar Ubuntu, que ya se encontraría disponible en el menú de Inicio. La primera vez que iniciamos, pide que creemos un usuario y una contraseña para el usuario UNIX, para tener los privilegios de administrador. 

### Cygwin: Unix en Windows
Para instalar **Cygwin** en nuestro ordenador personal, descargamos el producto de su [web](https://www.cygwin.com/).

Cuando ejecutamos el archivo instalador de **Cygwin** (`setup-x86_64.exe`) nos pregunta desde dónde queremos instalarlo, y seleccionamos la opción *Instalar desde Internet*. Lo siguiente será elegir dónde instalar **Cygwin**: desde [sus instrucciones](https://www.cygwin.com/faq.html#faq.setup.c) sugieren instalarla en una ramificación distinta a `C:\`, la raíz de Windows, pero para las que solo tenemos una partición dejamos la ruta establecida por defecto.

En la siguiente pantalla, **Cygwin** nos preguntará si queremos instalar paquetes antes de terminar la instalación.  Tras realizar esto tuvimos que instalar los paquetes siguientes: `libcurl4`, `wget`, `ca-certificates-letsencrypt`, `lynx`, `nano` y `openssl`. Para ello, le damos a la columna *New* de cada uno de los paquetes y seleccionamos la última opción/versión publicada. 

## 2. Configuración del programa

Una vez instalados, hemos configurado algunos parámetros tanto de WSL como de *Cygwin*, como algún alias, cambiar la *home* o configurar `git` para facilitarnos su uso.

### Establecer alias

Creamos un alias en la terminal para ahorrarnos escribir toda la ruta de nuestra carpeta entera. Así, en vez teclear, por ejemplo, `cd ‘/mnt/c/Users/usuaria/Documentos/Apuntes/Periodismo de Datos/’`, si tecleamos `micasa`, nos hará la misma acción y nos ahorraremos escribir toda la ruta.

Para ello, editamos el archivo de configuración de Bash. Está en el directorio «casa» u «hogar» de nuestro usuario: `$HOME/.bashrc`. 

Desde la línea de comandos de la terminal, introducimos el comando `echo` y entonces enviamos la salida con `>>` al final del archivo `.bashrc`: `echo “alias micasa=“cd ‘/mnt/c/Users/usuario/Documentos/Apuntes/Periodismo de Datos/’” >> $HOME/.bashrc`. De esta forma, cada vez accedamos a **Ubuntu** o **Cygwin**, al teclear el alias en la terminal nos llevará inmediatamente a la ruta que hemos asignado. Para poder ver el archivo de configuración del alias lo podemos hacer con `cat $HOME/.bashrc` y para poder modificarlo, si en algún momento lo vemos conveniente, con `nano $HOME/.bashrc`.

### Cambiar la home de Cygwin a la de Windows

En Cygwin, hemos cambiado la ruta de «hogar» o «casa» de nuestro usuario para que sea la de Windows. Para ello hemos editado el archivo `nsswith.conf` con `nano`: `nano /etc/nsswith.conf`. Al final del archivo, introducimos `db_home: windows`.

Guardamos con (CTRL + O) y cerramos con (CTRL + X). Cerramos Cygwin y volvemos a entrar para que se actualice. Para comprobarlo introducimos el comando `pwd`. Si hemos cumplido los pasos pertinentes, nos tendría que salir `/cygdrive/c/Users/usuaria`.


### Configurar git

Empecemos por definir qué es Git exactamente. Microsoft lo define como [“un sistema de control de versiones distribuido. Esto significa que un clon local del proyecto es un repositorio de control de versiones completo”.](https://docs.microsoft.com/es-es/devops/develop/git/what-is-git). Nosotramos utilizaremos `git` como nuestro software para el sistema de control y nos valdremos del comando `git` para poder vincular nuestra terminal con un repositorio remoto, es decir, el que estaría subido en GitHub.

Para ello, tenemos que ir a nuestra carpeta personal y allí clonar el repositorio de nuestro GitHub. En el repositorio copiamos el enlace https del código (la opción "*Code*") y lo clonamos en nuestra terminal con el comando: `git clone [url]` . Para comprobar que se nos ha clonado el repositorio remoto en nuestro directorio ejecutamos el comando `ls` que nos permitirá acceder al listado de archivos dentro del directorio. 

El siguiente comando a introducir es  `git config --global user.name [nombre del usuario de Github]` y a continuación `git config --global user.email [correo del usuario de Github]`. Ya lo tendríamos vinculado a nuestro perfil en GitHub.  Para guardar ejecutamos `git commit` y, con `git config --global set-editor nano`, escogemos que el editor de texto predeterminado sea siempre *nano*. 



## 3. Configuración de un programa de edición de texto

Para editar los textos de nuestros archivos desde la terminal nos serviremos de *nano*, el editor de texto en Linux. Tenemos que configurarlo primero, para que así el texto se adapte a la resolución de la pantalla predeterminada y que aparezca el número de líneas. Para esto hemos ejecutado`nano $HOME/.nanorc` y ponemos lo siguiente:

`# Ajustar el texto a pantalla`

`set softwrap`

`# Numerar las líneas`

`set linenumbers`

### Cygwin

Con Cygwin el proceso es un poco diferente. Primero hay que copiar el archivo de configuración de `nano` que se sitúa en el directorio `/etc`. De nuevo, al igual que hicimos en WSL, configuramos que aparezcan las líneas numeradas a través de `set linenumbers`. Guardamos con CTRL + O y salimos con CTRL + X.

## 4. Configuración y funcionamiento de un gestor de paquetes/programas del emulador de la terminal

Un gestor de paquetes es un grupo variado de instrumentos que sirven automatizan la instalación, actualización, configuración y eliminación de paquetes de software en sistemas Unix. En el caso de Ubuntu es `apt`, aunque Cygwin tiene el suyo propio, `apt-cyg`, que no viene por defecto con el programa sino que hay que instalarlo a parte.

Tenemos disponibles las instrucciones para instalarlo en [GitHub](https://github.com/transcode-open/apt-cyg#quick-start). Siguiendo esos pasos, primero lo instalamos ejecutando `lynx -source rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg` y luego `install apt-cyg /bin`.

A partir de ahí lo podemos usar para instalar herramientas, como `nano`, mediante la sintaxis `apt-cyg install herramienta`, como `apt-cyg install nano`.

## 5. Versión del lenguaje de SHELL

Para comprobar la versión del lenguaje de Shell utilizado ejecutamos la variable de entorno `$0`, que consultamos previamente con el comando `echo $0` que nos devolverá qué Shell utilizamos, que en nuestro caso seeía Bash. 

Para comprobarlo tenemos dos opciones usamos la variable de entorno `$BASH_VERSION`, a través de `echo`.

### Shell en Cygwin

`$ echo $0`

`-bash`

```$ echo $BASH_VERSION```
```4.4.12(3)-release```

`$ bash --version`
`GNU bash, version 4.4.12(3)-release (x86_64-unknown-cygwin)`


## 6. Valor de la variable de entorno PATH

Las variables de entorno, en nuestro caso la variable de entorno, sería `$PATH`, la variable propia de los sistemas de Microsoft. Si quisieramos ver el valor de la variable `PATH` lo hacemos con el comando `echo $PATH`. La terminal nos devuelve las rutas específicas donde se encuentran instalados los programas podemos ejecutar con la terminal.


## 7. Comandos utilizados y ejemplos

A lo largo del documento ya hemos visto algunos de los comandos utilizados para la instalación y gestión de funciones en la terminal, pero a continuación se recogerán otras que hemos aprendido y/o utilizado. 

Los comandos siempre mantienen la siguiente estructura: ***comando / opciones / argumentos***

 - `pwd` = en qué ruta nos encontramos
-  `ls` = listar un directorio
- `cd` = acceder a un directorio específico. Con `cd` nos dirige al directorio raíz, con `cd ..` sube un directorio y con `cd -` nos lleva al último sitio en el que estábamos.
- `mv`= mueve o corta las carpetas o archivos de sitio, pero también sirve para renombrarlos. Si queremos mover la carpeta de periodismo de datos (`/mnt/c/Users/usuario/Documentos/periodismo-de-datos`) a otro lado, ejecutamos `mv /mnt/c/Users/usuario/Documentos/periodismo-de-datos /mnt/c/Users/usuario/Documentos/Apuntes/` . Como vemos, después de `mv` escribimos la ruta de origen y lo siguiente es el directorio de destino. Si queremos renombrar ejecutamos `mv periodismo-de-datos nuevo-nombre`.
- `nano` = editar textos. Para editar con `nano`, tenemos que escribir `nano` seguido del nombre del archivo. Si estamos en la carpeta de la asignatura, por ejemplo, escribimos `nano README.md`. Para guardar CTRL + O, y para salir CTRL + X. 
- `cp [origen] [destino]` = copiar y pegar archivos.
- `man` = es el comando del manual de la terminal. `Q` para salir.
- `mkdir [nombre carpeta]` = creamos una carpeta
- `cat` = con este comando visualizamos un archivo desde la misma terminal. 
- `echo` = con este comando hacemos que la terminal nos devuelva un texto. Por ejemplo, si queremos saber cuál es nuestra variable de entorno home debemos poner `echo $HOME`. 
- `env`= visualizar en pantalla todas las variables de entorno. Si lo usamos con `| less`, es un visor más ameno porque son demasiadas variables y no caben en la pantalla: `env | less`. 
  - `touch`= crea un archivo nuevo. Por ejemplo, si queremos crear un README.md en nuestra carpeta, escribimos `touch README.md`.
  - `tree`= como `ls` pero con más opciones. Con `tree -L 1` le decimos cuántos niveles queremos ver. También podemos poner `tree -L 2` o `tree -L 3`, según el nivel de detalle.
  - `rm`= eliminar archivos o directorios. Hay que tener cuidado porque los elimina de forma definitiva, los archivos no van a la papelera.
  - `wget`= descargar un archivo/contenido de una web. Tenemos que copiar el enlace de lo que nos queramos descargar. 
  - `curl`= igual que wget pero con más opciones. 
**Comandos de Git** 
- `git clone` = comando con el que clonamos un repositorio remoto en nuestro directorio local.
- `git config` = con este comando definimos los valores de configuración de git.Como hemos visto anteriormente: `git config --global user.name`;  `git config --global user.email`;  `git config --global set-editor nano`.
- `git status` = comando que nos muestra el estado del directorio de trabajo y del área de entorno. Nos permite ver los cambios que se han realizado, los que se han reparado o no, en los que Git no puede vincular, etc. 
- `git add “nombre-archivo”` o `git add .` = este comando nos permite añadir los cambios del directorio al entorno de ensayo, es decir con este comando le dices a Git las actualizaciones que quieres realizar. A través del argumento `.` añades todos los nuevos archivos, cambios etc. 
- `git commit -m “lo que comiteamos” ` o `git commit .` = con este comando realizamos el commit es decir el cambio que hemos realizado se verá con esta acción en GitHub. A través del argumento `.` añades todos los nuevos archivos, cambios etc. 
- `git push` =  se usa este comando para cargar el contenido del repositorio local al repositorio remoto de Github (en nuestro caso) . Este paso es el último que realizaremos para actualizar los cambios que veíamos en `Git Status`.
- `git pull` =  permite actualizar los contenidos de los repositorios. 
