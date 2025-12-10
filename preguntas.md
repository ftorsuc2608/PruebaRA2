# 🧠 Examen RA2  -  Preguntas del examen 

## Ejercicio 1  
### 1A. Pregunta
¿Por qué NO se centra el texto del `<h1>` en este caso? Explícalo con tus palabras. (por qué visual y estructuralmente no aparece centrado entre el borde izquierdo y el menú)  
  
>Porque `text-align` centra el texto dentro del elemento, no centra la posición del elemneto en sí, para eso se deben utilizar Flexbox o Grid.

### 1B. Ejercicio - Soluciona de dos formas diferentes
#### Solución con FlexBox
>Cuando usamos display: flex en el contenedor, si colocamos el título en medio pero hay otros elementos (como el menú a la derecha), el `<h1>` no queda centrado naturalmente, para ello debemos definir su tamaño con `flex:X;`
```css
  .site-header {
    display: flex;                    /*Convierte el contenedor en un Flexbox*/
    align-items: center;
    background-color:yellowgreen;
    border:2px solid black;
    box-shadow: 5px 5px black;
    padding:10px;
  }

  h1 {
    flex:1;                           /*Ocupará todo el espacio disponible*/
    text-align: center;
  }
```
#### Solución con CSS Grid
>El `<h1>` queda centrado porque está en la columna central de la cuadrícula.
```css
  .site-header {
    background-color:yellowgreen;
    border:2px solid black;
    box-shadow: 5px 5px black;
    padding:10px;
}

  h1 {
    display: grid;                    /*Convierte el contenedor en un Grid*/
    justify-items: center;            /*Centra el contenido horizontalmente dentro de cada celda*/
    align-items: center;              /*Centra el contenido verticalmente dentro de cada celda*/
}
```

### 1C. Ejercicio – Convertir la cabecera en dos filas
Sin modificar el HTML, debes conseguir mediante CSS que la cabecera se reorganice de la siguiente forma:

* En la **primera fila** se muestra solo el `<h1>`, centrado horizontalmente
* En la **segunda fila** se muestra el menú de navegación (`<nav class="main-nav">`), también centrado horizontalmente.
* Ambos elementos forman parte del **mismo header**, solo cambia la distribución.
* Entre la fila del `h1` y la fila del menú debe haber exactamente 30px de separación vertical *(No puedes añadir etiquetas nuevas en el HTML. Solo se permite modificar el CSS)*
Escribe el **CSS necesario** para conseguir esa estructura.
```css
  .site-header {
    display: grid;                          /*Convierte el header en un grid*/
    grid-template-columns: auto 1fr auto;   /*Define 3 columnas*/
    grid-template-rows: auto auto;          /*Define 2 filas de tamaño automático*/
    align-items: center;                    
    justify-items: center;
    row-gap: 30px;                          /*Espacio vertical de 30px entre la primera y segunda fila*/
    background-color: yellowgreen;
    border: 2px solid black;
    box-shadow: 5px 5px black;              
    padding: 10px;
  }

  .site-header h1 {
    grid-column: 2;  
    grid-row: 1;     
    margin: 0;
  }

  .site-header .main-nav {
    grid-column: 2;                         /*Se posiciona el menú en la segunda columna*/
    grid-row: 2;                            /*Se posiciona el menú en la segunda fila*/
  }

  .site-header button {
    grid-column: 1;
    grid-row: 2;
  }
```
### 1D. Ejercicio – Dar relieve y separación visual al header
Se pretende que la cabecera del sitio (.site-header) tenga un aspecto más definido y se diferencie claramente del resto de la página.  
Debes conseguir, únicamente con CSS, que:  
  
* La cabecera tenga un color de fondo distinto al del resto de la página  
```css
  .site-header {
    display: flex;
    align-items: center;
    background-color:yellowgreen;   /*Cambia el color de fondo*/
}
```
* Haya una separación visual clara con el contenido que va debajo (por ejemplo, usando un borde inferior y una sombra)  
```css
    .site-header {
    display: flex;
    align-items: center;
    background-color:yellowgreen;
    border:2px solid black;          /*Crea un borde sólido, negro de 2px*/
    box-shadow: 5px 5px black;       /*Crea una sombra*/
}
```
* El contenido del header tenga un espaciado interior adecuado para que no quede “pegado” a los bordes.
```css
    .site-header {
    display: flex;
    align-items: center;
    background-color:yellowgreen;
    border:2px solid black;
    box-shadow: 5px 5px black;
    padding:10px;                   /*Espaciado interior*/
}
```
## Ejercicio 2 — Reorganización del header con tres elementos  
### 2A. Ejercicio
Cambia tu HTML para introducir el botón dentro de header
```html
    <header class="site-header">
            <button>btn</button>  <!--Etiqueta de botón-->
            <h1>Mi Sitio Web</h1>

            <nav class="main-nav">
                ...
            </nav>
    </header>
```
### 2B. Ejercicio

Indica el CSS necesario para maquetar este diseño usando:

* ✔ **Flexbox** (obligatorio)
```css
  .site-header {
    display: flex;                    /*Convierte el elemento en un Flexbox*/
    align-items: center;              /*Centra el eje transversal*/
    justify-content: space-between;   /*Centra el eje principal*/
    background-color:yellowgreen;
    border:2px solid black;
    box-shadow: 5px 5px black;
    padding:10px;
  }

  h1 {
    flex: 1;                          /*Define el tamaño del Flexbox*/
    text-align: center;
  }
```
* ✧ Grid (opcional, pero lo valoraré positivamente si conoces cómo hacerlo)
```css
  .site-header {
    display:grid;                           /*Convierte el elemento en un Grid*/
    grid-template-columns: auto 1fr auto;   /*Define 3 columnas*/
    align-items:center;                     /*Centra el eje transversal*/
    background-color:yellowgreen;
    border:2px solid black;
    box-shadow: 5px 5px black;
    padding:10px;
  }

  h1 {
    text-align: center;
  }
```

## Ejercicio 3 — Miniaturas, zoom y enlace a la imagen original  
  En tu galería de imágenes, debes realizar lo siguiente:  
### 3A. Crear miniaturas  
  Genera nuevas imágenes pequeñas (por ejemplo 200px de ancho aprox.). Debes reemplazar las imágenes de la galería por estas miniaturas.  
```css
  figure a img{  
  width:250px;                          /*Define el ancho de la miniatura*/
  height:300px;                         /*Define la altura de la miniatura*/
  display:table-row;                    /*El elemento adopta el comportamiento de una fila de tabla*/
  border-radius: 5%;                    /*Define el radio del borde*/
  box-shadow: 15px 5px #470C00;         /*Define la sombra*/
}  
```
>  Se han creado versiones más pequeñas de las imágenes con unas dimensiones de 250x300px.  

### 3B. Efecto hover  
Al pasar el ratón por encima:
* Debe haber zoom suave (por ejemplo usando transform: scale(1.1);)
* Debe aparecer un marco, sombra o borde (elige tú el estilo)
```css
  a img:hover{                          /*Comportamiento cuando el cursor está sobre el elemento*/
  width:500px;                          /*Define ancho más grande*/
  height:600px;                         /*Define altura más grande*/
  transform: scale(1.2);                /*Produce un cambio de tamaño suave*/
  border-radius: 7%;  
  box-shadow: 15px 5px #A31B00;  
}  
```
  Se puede ver en el código el zoom suave y el cambio en la sombra de la imagen.  

### 3C. Enlace a la imagen original
Al hacer clic en la miniatura, la imagen original (de mayor tamaño) debe abrirse en otra pestaña.  
Tu tarea consiste en:
* Escribir el HTML corregido
```html
        <div id="frame">
          <figure>
            <a href="img/arcade.jpg" target="_blank"><img src="img/arcade.jpg" alt="Máquinas Arcade"></a>
          </figure>
          <figure>
            <a href="img/nes.jpg" target="_blank"><img src="img/nes.jpg" alt="Nintendo Entertainment System"></a>
          </figure>
          <figure>
            <a href="img/n64.jpg" target="_blank"><img src="img/n64.jpg" alt="Nintendo 64"></a>
          </figure>
          <figure>
            <a href="img/ps1.jpg" target="_blank"><img src="img/ps1.jpg" alt="Play Station"></a>
          </figure>
          <figure>
            <a href="img/xbox.jpg" target="_blank"><img src="img/xbox.jpg" alt="XBox"></a>
          </figure>
          <figure>
            <a href="img/pc.jpg" target="_blank"><img src="img/pc.jpg" alt="PC"></a>
          </figure>
          <figure>
            <a href="img/wii.jpg" target="_blank"><img src="img/wii.jpg" alt="Wii"></a>
          </figure>
          <figure>
            <a href="img/metaquest.jpg" target="_blank"><img src="img/metaquest.jpg" alt="Meta Quest"></a>
          </figure>
       </div>
```
> Las imágenes se abrirán en una pestaña nueva debido a la propiedad  `target="_blank"`
* Escribir el CSS que genera el zoom + marco 
```css
a img:hover{  
  width:500px;  
  height:600px;  
  transform: scale(1.2);  
  border-radius: 7%;  
  box-shadow: 15px 5px #A31B00;  
}  
```
* Incluir una captura en tu informe de evidencias mostrando el resultado  
  
>Podemos ver que el efecto del hover funciona correctamente:  
![alt text](image.png)  

>Y la imagen se muestra en una pestaña nueva como podemos ver en la imagen:  
![alt text](image-1.png)

## Ejercicio 4 — Informe de evidencias del proyecto (defensa técnica simple)
### Introducción
Explica en 4–6 líneas:  
* El tema de tu web  
* Qué contenido has incluido  
* Cuál era tu idea de diseño  
  
>  Mi intención era crear una web para conservar los videojuegos más relevantes a nivel histórico con el fin de que puedan seguirse disfrutando y estudiando. He incluido varias secciones, en las que se habla de la historia de los videojuegos y las consolas que les dan soporte.

### Evidencias de HTML5
Incluye capturas y explicaciones breves del uso de:
* Header, main, section, footer
>**HEADER**  
Se utiliza la etiqueta `header` para crear un elemento de tipo cabecera, conteniendo los elementos del navegador.  
![alt text](image-2.png)  
<br>
**MAIN**
Se utiliza la etiqueta `main` para crear un elemento cuyo contenido es el principal, separándolo de otros elementos repetitivos como `nav`.
![alt text](image-3.png)  
<br>
**SECTION**
La etiqueta `section` se usa para dividir el contenido en secciones temáticas claramente diferenciadas dentro de una página o documento.  
![alt text](image-4.png)  
<br>
**FOOTER**
La etiqueta `footer` define el pie de página de una página web o de una sección concreta.
![alt text](image-5.png)  

* El menú superior
> El menú superior está formado por una etiqueta `nav` que contiene una lista con los enlaces internos necesarios para que la navegación por la página sea posible.  
![alt text](image-6.png)
* El menú lateral ☰
> El menú lateral ☰ está formado por un `button`, que sirvirá para mostrar y ocultar el menú lateral cada vez que sea pulsado, y un `nav`, que compondrá el menú deslizante.    
![alt text](image-7.png)
* La sección Hero
> Hero es la sección principal y más destacada que aparece al inicio de una página web  
![alt text](image-8.png)
* La tabla
> La tabla está formada por etiquetas `table` para definir la tabla, `thead` para definir la cabeza de la tabla, `tbody` para el cuerpo, `th` para las celdas de encabezado, `tr` para las filas y `td` para las columnas.
![alt text](image-9.png)
* El formulario
> El formulario está compuesto por una etiqueta `form`, que contiene los elementos del formulario.  
![alt text](image-10.png)
* La galería de imágenes
> Para la galería he creado un contenedor con la etiqueta `div` y he introducido las etiquetas `figure` que contienen el enlace con la imagen.
![alt text](image-11.png)
* Enlaces internos y externos
>**INTERNOS**  
Se utiliza el identificador de la sección para la dirección del enlace.
![alt text](image-12.png)  
**EXTERNOS**  
Antes de realizar el examen, mi página sí tenía enlaces externos como el que se muestra en la imagen, pero he tenido que modificarlo para que los enlaces apunten a las propias imágenes. Se utilizaba la url del sitio que se deseaba visitar.
![alt text](image-13.png)

### Evidencias de CSS
Incluye ejemplos de código mostrando:
* Selectores utilizados (tipo, clase, id, descendente…).
```css
  /*Selector de tipo*/
    body {
      font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
      margin-left:230px;
      margin-top:-50px;
      padding:5px;
      background-color:#D12300;
    }

  /*Selector de clase*/
    .site-footer {
      background-color: black;
      width:1460px;
      padding:10px;
      color:white;
    }

  /*Selector de id*/
    #misionimg {
      width:950px;
      height:700px;
      margin-left:260px;
    }

  /*Selector descendente*/
    figure a img{
      box-shadow: 15px 5px #751400;
    }
  
  /*Selector de grupo*/
    h2, h3 {
      text-align: center;
      margin: 5px;
      font-family:"SuperChiby",sans-serif;
    }
```
* Pseudoclases
```css
  /*Selector de pseudoclase*/
    a img:hover{
      width:500px;
      height:600px;
      transform: scale(1.2);
      border-radius: 7%;
      box-shadow: 15px 5px #A31B00;
    }
  
  /*Selector de pseudoelemento*/
    tr td:first-of-type{
      font-weight:bold;
    }
```
* Flexbox o Grid en alguna parte
```css
    figure{
      display:inline-grid;          /* Hace que <figure> se comporte como un contenedor grid, pero ocupando solo el espacio necesario (en línea). */
      margin: 3.5%;                 /* Agrega un margen alrededor del elemento del 3.5% respecto al ancho del contenedor*/
      align-items:center;           /* Centra verticalmente el contenido dentro del grid. */
    }
```
* Uso de sombras (box-shadow) o cards
```css
  figure a img{
    box-shadow: 15px 5px #751400;
  }
```
* Estilos de tus menús
Explica qué has intentado conseguir con ese diseño
> Mi intención ha sido en todo momento maquetar mi página de una forma coherente, atravctiva, limpia y minimalista, utilizando una paleta de colores cálidos que pueda diferenciar de forma fácil (debido a mi daltonismo), presentando la información de forma central y clara a lo largo de la página.

### Fuentes utilizadas
Debes explicar:
* Qué fuente local has incluido (@font-face)
```css
  @font-face {
    font-family: 'SuperChiby'; 
    src: url('/../font/SuperChiby.ttf') format('truetype');
    font-weight: normal; 
    font-style: normal;
    font-display: swap;
  }
```
* Qué fuente online has añadido (Google Fonts)
```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Condensed:ital,wght@0,100..900;1,100..900&display=swap" rel="stylesheet">
```
* Por qué te han gustado esas tipografías
> Me han gustado estas tipografías porque no son exageradamente extravagantes y son monospace, por lo que todas las letras ocupan el mismo tamaño, evitando descuadres.

### Menú lateral: breve explicación
No tienes que explicar JavaScript en detalle. Solo:
* Qué ocurre al pulsar el botón
> Al pulsar el botón se activa el event listener que muestra el menú lateral.
* Qué clase cambia
> La clase que cambia es `.open-menu`.
* Cómo se mueve el menú con CSS
> Con una transformación suave que se activa mediante el javascript.

### Conclusión personal
Explica:
* Qué has aprendido
> He aprendido a utilizar Flexbox y Grid, y he repasado conceptos básicos fundamentales para la maquetación de páginas web como el uso correcto de etiquetas semáticas y el uso de los selectores CSS.
* Qué te gustaría mejorar
> Me gustaría ser capaz de utilizar Flexbox y Grid sin tanta dificultad, para lo que trabajaré más los conceptos en mi tiempo libre.
* Qué ha sido lo que más te ha costado
> Lo que más me ha costado ha sido el uso de Flexbox y Grid, y `@font-face` no funciona, no sé por qué. 
* Qué parte de tu web te gusta más
> Mi parte favorita es la de la galería, es a la que más tiempo le he dedicado por el uso de Grid, por lo que es la que más tiempo de trabajo tiene y también la que tiene más efectos visuales.


