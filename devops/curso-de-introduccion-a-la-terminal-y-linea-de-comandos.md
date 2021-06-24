# Curso de Introducción a la Terminal y Linea de Comandos

## ¿Qué es la terminal? 

Es una herramienta indispensable para los desarrolladores y estas son las razones

1. Tiene mucha **flexibilidad,** con unos cuantos comandos bien escritos y estructurados podemos ejecutar procesos en nuestras computadoras de una manera eficaz. \(Mover archivos, hacer copias, backups, o implementar procesos que se ejecuten de forma automática cada cierto tiempo\)
2. Hacer los procesos desde terminal tiende a ser mucho más **rápido** que si lo hacemos de forma habitual mediante una interfaz grafica 
3. No siempre tenemos disponible una interfaz grafica, existen muchos casos de uso, por ejemplo al configurar un servidor remoto.
4. Si no sabemos usar la terminal de forma correcta podemos invocar demonios.

La terminal es una interfaz grafica que simula una linea de comandos , es decir, la terminal es la ventana que aloja la shell o linea de comandos, esta es un programa que toma los comandos y los pasa al SO para que realice determinada acción.

#### Tipos de Shell

* Bourne Shell
* Bash Shell \(Linux\)
* Z Shell \(Mac\)
* C Shell
* Korn Shell
* Fish Shell
* PowerShell \(Windows\) 

{% hint style="info" %}
Un comando es un programa que se puede ejecutar desde la terminal.
{% endhint %}

## Aprendiendo a caminar en la terminal

### Sistema de archivos

![](../.gitbook/assets/image%20%2814%29.png)

> En la carpeta 📁 `home` se encuentran los usuarios del SO.

### Comandos Básicos

| Comando | Descripción |
| :--- | :--- |
| `ls` | Lista los archivos y directorios. |
| `ls -l` | Lista los archivos con toda su info |
| `ls -lh` | Lista los archivos con toda su info legible para los humanos |
| `ls -la` | Lista los archivos incluso los archivos ocultos |
| `ls -lS` | Lista los archivos y los ordena por peso |
| `ls -lr` | Lista los archivos en orden alfabético inverso |
| `tree` | Lista los archivos en visualización de árbol |
| `tree -L {#}` | Visualización en árbol a la profundización indicada |
| `cd` | Se traslada a`home` |
| `cd {folder}` | Se traslada a `/folder` |
| `clear` o `ctrl+L` | Limpia la consola |
| `pwd` | Imprime la ruta en la cual nos encontramos posicionados |
| `file {archivo}` | Describe el tipo de archivo que le pasamos como parámetro |

### Rutas

* Rutas absolutas: Son las rutas que especifican puntualmente una dirección ej : `home/kathe/Platzi/`
* Rutas relativas: Son rutas que pueden variar dependiendo de la dirección en la que estemos. 
  * `.` Esta ruta se refiere a la dirección actual
  * `..` Esta ruta se refiere a al directorio que contiene la ruta actual

## Manipulando archivos y directorios

| Comando | Descripción |
| :--- | :--- |
| `mkdir {folder}` | Creación de directorio |
| `touch {file}` | Creación de archivos |
| `cp {origin_file} {new_file}` | Copiar archivo en el mismo folder |
| `mv {file} {path}` | Mover un archivo a otro folder |
| `mv {name_file} {new_name_file}` | Renombrar un archivo |
| `rm {archivo}` | Eliminar un archivo |
| `rm -i {archivo}` | Elimina el archivo de forma intuitiva |
| `rm -r {folder}` | Eliminar un directorio |

## Explorando el contenido de nuestros archivos

| Comando | Descripción |
| :--- | :--- |
| `head {archivo}` | Visualiza las 10 primeras líneas del archivo |
| `head {archivo} -n {#}` | Visualiza las primeras \# líneas del archivo |
| `tail {archivo}` | Visualiza las 10 ultimas líneas del archivo |
| `tail {archivo} -n {#}` | Visualiza las ultimas \# líneas del archivo |
| `less {archivo}` | Visualiza el srchivo e internamente permite la busqueda de palabras |
| `xdg-open {archivo}` | Abre el archivo con el programa predeterminado  |
| `nautilus {ruta}` | Abre el explorador de archivo con la ruta indicada |

## ¿Qué es un comando?



