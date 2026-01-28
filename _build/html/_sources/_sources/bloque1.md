Materiales de Matemáticas Discretas
===============================

Universitat d'Alacant, curso 2023–2024
--------------------------------------

## Guía de como usar Jupyter Book
Esto es un pqueño tutorial de como usar Jupyter Book para crear un libro de texto web. Para ello veremos las principales funcionalidades de Jupyter Book y como usarlas.
### IDE
Desde la terminal, dirigete a la carpeta donde tengas el libro. Un vez estes ahi, ejecuta el siguiente comando:
```bash
code .
```
Esto abrira el IDE de Visual Studio Code en la carpeta donde tengas el libro. Desde aqui podras editar los archivos del libro.
### Organización de los archivos
Una vez abierto el editior, veras que hay una serie de archivos y carpetas.
- _config.yml: Archivo de configuración del libro. Aqui se configuran cosas como el nombre del libro, el autor, el tema, etc. Aconsajamos no tocar este archivo.
- _toc.yml: Archivo que contiene la estructura del libro. Aqui se configuran los capitulos y secciones del libro. Hablaremos mas de este archivo mas adelante.
- _build: Carpeta que contiene los archivos generados al compilar el libro. Dentro de esta carpeta encontraremos los archivos html del libro, concretamente si nos vamos a la carpeta html, index.html es el archivo que contiene el libro. Si ejecutamos este archivo, se nos abrira el libro en el navegador.
- intro.md: Archivo root del libro. Aqui se encuentra la introducción del libro. A partir de aqui se enlazan los demas archivos.
- references.bib: Archivo que contiene las referencias bibliograficas del libro. Aqui se añaden las referencias que se quieran citar en el libro.
- resto de archivos: El resto de archivos son los capitulos y secciones del libro. Estos archivos se añaden en el archivo _toc.yml. Hablaremos mas de este archivo mas adelante.

### Añadir capitulos y secciones
Para añadir capitulos y secciones al libro, debemos editar el archivo _toc.yml (Previamente se tiene que haber creado el fichero.md con la información que se quiere meter. La metodología a seguir es el crear un archivo bloqueX.md, el cual tenga una pequeña introducción de que se va a ver en el bloque. Una vez creado, todos los subapartados del bloque deberían llevar el nombre de bloqueX_el_nombre_que_quieras_poner). Este archivo tiene la siguiente estructura:
```yml
format: jb-book # No tocar
root: intro # No tocar
defaults: # No tocar
  numbered: true # No tocar
parts: # Partes del libro
- caption: Bloque 1 # Nombre de la parte
  chapters: # Capitulos del bloque
  - file: bloque1 # fichero que contiene contenido
  - file: bloque1_Introduccion # fichero que contiene contenido
- caption: Bloque kk # Nombre de la parte
  chapters: # Capitulos del bloque 
  - file: markdown # fichero que contiene contenido
  - file: notebooks # fichero que contiene contenido
  - file: markdown-notebooks # fichero que contiene contenido
```
Como se puede ver, cada vez que queramos añadir un capitulo o seccion, debemos añadirlo tal y como muestra la distribución del archivo.
### Urls, citas, imagenes y tablas
#### Urls
Para añadir una url, se debe usar la siguiente sintaxis:
```md
[texto del enlace](url)
``` 
#### Citas
Hemos quedado en meterlas a mano con bullets tal que asi:
```md
- [1] Autor, Título, Año
- [2] Autor, Título, Año
```
#### Figuras
Para añadir una figura, se debe usar la siguiente sintaxis:
````md
```{figure} ruta_de_la_imagen
---
name: nombre_de_la_imagen
width: 400px
align: center
height: 200px
---
Fancy caption for **nombre_de_la_imagen**.
```
````
Un ejemplo de la imagen con nuestro logo:

```{figure} ./images/bloque1/logos.jpeg
---
name: logo
width: 400px
align: center
height: 200px
---
Fancy caption for **logo**.
```
Mira la figura {numref}`logo`. De esta forma metemos la referencia a la imagen.

#### Tablas
Para añadir una tabla, se debe usar la siguiente sintaxis:
```md
| Cabecera 1 | Cabecera 2 |
| ---------- | ---------- |
| Celda 1    | Celda 2    |
| Celda 3    | Celda 4    |
```
Dando com resultado:
| Cabecera 1 | Cabecera 2 |
| ---------- | ---------- |
| Celda 1    | Celda 2    |
| Celda 3    | Celda 4    |

#### Código
Para añadir código, se debe usar la siguiente sintaxis:
```{code-block} python
---
linenos: true
---
import numpy as np
import matplotlib.pyplot as plt
import networkx as nx
print("Hello world!")
```

#### Compilar el libro
Para compilar el libro, debemos ejecutar el siguiente comando en la terminal:
```bash
jupyter-book build ./
```
Un vez compilado se te generara un archivo html en el directorio _build/html/index.html. Si abres este archivo, se te abrira el libro en el navegador.