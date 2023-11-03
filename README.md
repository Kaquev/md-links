
# mdlinks 
` Analizador de enlaces en archivos Markdown`


## Índice

- [1. Sobre el proyecto](#1-resumen-del-proyecto)
- [2. Consideraciones técnicas](#2-Instalacion)
- [3. Usabilidad](#3-Uso)
- [4. Resumen](#4-Resumen)

---

## 1. Sobre el proyecto

mdlinks es una herramienta de línea de comandos y una librería de Node.js que te permite analizar archivos Markdown en busca de enlaces (URLs) y reportar estadísticas sobre ellos. Esta herramienta es útil para verificar la integridad de los enlaces en tus documentos Markdown, identificar enlaces rotos y obtener información sobre los enlaces, como su estado y texto anclado.

 Su desarrollo fue en Node.js (En este proyecto no fue  permitido utilizar async/await) 

## 2. Instalacion

Para instalar mdlinks ingresa esta linea de comando en tu terminal:

`npm install kaquev/md-links`


## 3. Uso

Para analizar un archivo Markdown y obtener un informe de los enlaces contenidos en él, ejecute el siguiente comando en su terminal:

mdlinks ./example/archivodeprueba.md

La librería procesará la información y devolverá:

Una ruta absoluta del archivo.
Confirmación o negación de la existencia del archivo en la computadora.
Un arreglo de archivos Markdown encontrados.
Cada archivo Markdown encontrado contendrá las siguientes propiedades:

- file: Ruta del archivo donde se encontró el link.
- href: URL encontrada.
- text: Texto que aparecía dentro del link (<a>)

######  Ejemplo:

- ./example/archivodeprueba.md https://www.google.com Google

Podemos observar que me entrega las propiedades mencionadas.

- file: ./example/archivodeprueba.md
- href: https://www.google.com
- texto: Google


##### Podemos realizar busquedas de directorios y de subdirectorios  y de igual manera acceder a sus enlaces.

######  Ejemplo:


**mdlinks ./example**
accedimos a 2 subdirectorios del directorio example y a sus enlaces.

C:\Users\anonimo\Desktop\Proyecto\md-links\example\archivodeprueba.md
./example https://www.google.com Google

C:\Users\anonimo\Desktop\Proyecto\md-links\example \subfiles\file2.md

C:\Users\anonimo\Desktop\Proyecto\md-links\example \subdos\prueba1.md
./example https://www.google.com Google




#### Opciones

Puedes usar las opciones  `--validate `para verificar la validez de los enlaces y`--stats`para obtener estadísticas sobre los enlaces.


Si pasamos la opción `--validate` el módulo debe hacer una petición HTTP para averiguar si el link funciona o no. Si el link resulta en una redirección a una URL que responde ok, entonces consideraremos el link como ok.

######  Ejemplo:

**mdlinks ./example/archivodeprueba.md `--validate`**

Resultado:
Vemos que el output en este caso incluye la palabra ok o fail después de la URL, así como el status de la respuesta recibida a la petición HTTP a dicha URL.

- ./example/archivodeprueba.md https://www.google.com Google 200 ok
- ./example/archivodeprueba.md https://www.openai.com OpenAI 200 ok
- ./example/archivodeprueba.md https://github.com GitHub 200 ok

Si pasamos la opción `--stats `el output (salida) será un texto con estadísticas básicas sobre los links.

######  Ejemplo:

**mdlinks ./example/archivodeprueba.md `--stats`**

Resultado:

- Cantidad de links: 3
- Enlaces únicos: 3

También podemos combinar` --validate` y `--stats` para obtener estadísticas que necesiten de los resultados de la validación.

 mdlinks ./example/archivodeprueba.md `--validate` `--stats`


- Enlaces válidos: 3
- Enlaces rotos: 0
- Cantidad de links: 3
- Enlaces únicos: 3




## 4-Resumen

| Comando | Descripcion                  |
| ------------- | ------------------------------ |
|   ` npm install Kaquev/md-links`  | Para instalar      |
| `mdlinks `   | **Para comenzar a utilizar** escribir el comando mdlinks (espacio) y el archivo/directorio queremos revisar    |
|   ` --validate `  | Para verificar la validez de los enlaces  (si el link funciona o no)   |
|   ` --stats `  | Muestra estadísticas sobre los enlaces encontrados en el archivo.   |


