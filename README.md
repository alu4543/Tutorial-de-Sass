# Sistemas y Tecnologías Web
## Tutorial de Sass
### 1 introducción
Sass acrónimo de (Syntactically Awesome StyleSheets)
Es un preprocesador de CSS que añade características muy potentes y elegantes.
Sass incluye las siguientes características:
* 100% compatible con CSS3.
* Permite el uso de variables, anidamiento de estilos, importación de hojas de estilos y mixins, gracias a la librería Compass.
* Incluye numerosas funciones para manipular con facilidad colores y otros valores.
* Permite el uso de elementos básicos de programación como las directivas de control y las librerías.
* Genera archivos CSS bien formateados y permite configurar su formato.


  ![media](media/media1.png)

### 2 Pre-instalación
Para usar Sass es necesario tener instalado Ruby. La instalación es un proceso bastante sencillo.

####.2.1 Linux
Si estás usando una distribución de Linux, Puedes instalar Rubi a través del gestor de paquetes apt , rbenv o RVM .

      $ sudo apt-get install ruby-full rubygems1.8

####.2.2 Windows
La manera más sencilla de instalar Rubi en  Windows es utilizar **[Ruby Installer.](http://rubyinstaller.org )**  
El programa de instalación también instalará Ruby command line powershel que le permitirá utilizar librarias de Ruby.

####.2.3 Mac
¡Felicidades!
Ruby viene pre-instalado.

### 3. instalación de Sass
Aquí está la forma más sencilla para empezar a utilizar Sass mediante el uso de la línea de comandos :
Rubí utiliza gemas para gestionar sus diversos paquetes de código como Sass.
#### 3.1 Comandos para la instalación

      $ gem install sass

Es bastante mágico, este comando instalará Sass y las dependencias necesarias. 
Si recibe un mensaje de error, entonces es probable que usted tendrá que utilizar el comando sudo para instalar la gema Sass . Se vería así :

      $ sudo gem install sass

Ahora deberíamos tener Sass instalado, pero nunca esta de más una pequeña verificación. Ejecutamos :

      $ sass -v

Te debe devolver algo parecido a este mensaje :
      Sass 3.4.20 (Selective Steve)
      ¡Felicidades! Usted ha instalado con éxito Sass.
      
¿Eres nuevo en Sass? 
No te te procupes, aprender bastante rápido.

### 4. Complación
El codigo escrito en Sass se compila mas adelante para obtener el codigo CSS para que los navegadores lo puedan leer.

#### 4.1 Desde consola
Para ejecutar Sass desde la línea de comandos, sólo tiene que ejecutar:

      $ sass main.sass style.css

#### 4.2 Vigilar (Watch)
También puede decirle a Sass que vegile el archivo Sass y actualizar el CSS cada vez que el archivo Sass cambie :

      $ sass --watch main.sass:style.css
      
#### 4.3 Vigilar un directorio
Pero si usted tienes un directorio con muchos archivos Sass, también puede decirle Sass para ver todo el directorio :

      $ sass --watch app/sass:public/stylesheets

### 5 Conversión y compatibilidad de sintaxis
Una de las ventajas de Sass es que los archivos creados con una sintaxis pueden importar cualquier archivo creado con la otra sintaxis.
Además, disponemos de una utilidad para la línea de comandos que te permite convertir una sintaxis en otra:

#### 5.1 Convierte un archivo Sass en SCSS

      $ sass-convert estilos.sass estilos.scss
 
#### 5.2 Convierte un archivo SCSS en Sass

      $ sass-convert estilos.scss estilos.sass

### 6. Variables
las variables puede almacenar cosas como colores ,fuente o cualquier valor CSS que querremos ruetilizar a lo largo de la hoja de estilo.
Sass usa el símbolo $ para las variables, a continuación un ejemplo :
#### 6.1 Ejemplo

    $fuente:    Helvetica, sans-serif
    $rojo: #FF0000
    body
      font: 100% $fuente
      color: $rojo

Cuando se procesa el Sass ,toma las variables que definimos $fuente y $rojo y genera la salidas CSS con nuestros valores de las variables puestas en la CSS.
Esto puede ser muy útil cuando se trabaja con los colores de una marca y los mantiene constante a través del sitio.
#### 6.2 CSS Generado

    body {
      font: 100% Helvetica, sans-serif;
      color: #FF0000;
    }

### 8. Nesting (Anidamiento)
#### 8.1 ¿Que es Anidamiento?
Notamos que al escribir HTML tiene una jerarquía anidada visual y clara . CSS, por otra parte, no lo hace .
Sass le permitirá a CSS que siga la misma jerarquía visual de su HTML.
#### 8.2 Advertencia
En general se considera una mala práctica crear reglas excesivamente anidadas, podría resultar difícil de mantener, 
Con esto en mente, a continuación un ejemplo :
#### 8.3 Ejemplos
    nav
      ul
        margin: 0
        padding: 0
        list-style: none
      li
        display: inline-block
      a
        display: block
        padding: 6px 12px
        text-decoration: none


You'll notice that the ul, li, and a selectors are nested inside the nav selector. This is a great way to organize your CSS and make it more readable. When you generate the CSS you'll get something like this:

    nav ul {
      margin: 0;
      padding: 0;
      list-style: none;
    }
    nav li {
      display: inline-block;
    }
    nav a {
      display: block;
      padding: 6px 12px;
      text-decoration: none;
    }

### 9 Partials
#### 9.1 Fragmentación de código
Se pueden crear archivos parcialesque contienen pequeños fragmentos de CSS que se pueden incluir en otros archivos Sass.
#### 9.2 CSS modularizado.
Esta es una buena practica para modularizar el CSS y ayudar a mantener las cosas más fáciles de mantener.
#### 9.3¿que es un parcial?
Un parcial es simplemente un archivo Sass llamado con un subrayado inicial algo así como _partial.scss .
El subrayado permite a Sass sabe que el archivo es un archivo solamente parcial y que no debe ser generado en un archivo CSS. Parciales Sass se utilizan con la directiva import .

### 10 Import
CSS has an import option that lets you split your CSS into smaller, more maintainable portions. The only drawback is that each time you use @import in CSS it creates another HTTP request. Sass builds on top of the current CSS @import but instead of requiring an HTTP request, Sass will take the file that you want to import and combine it with the file you're importing into so you can serve a single CSS file to the web browser.
Let's say you have a couple of Sass files, _reset.scss and base.scss. We want to import _reset.scss into base.scss.

#### 10.1 Ejemplos

    // _reset.sass
    html,
    body,
    ul,
    ol
      margin:  0
      padding: 0
      
      
    // base.sass
    @import reset
    body
      font: 100% Helvetica, sans-serif
      background-color: #efefef


Nótese que estamos usando import 'reset' ; en el archivo base.scss . Al importar un archivo que no es necesario incluir el .scss extensión de archivo .
Sass es inteligente y va a averiguarlo por ti. Al generar el CSS que obtendrá :


#### 10.1 Ejemplos

    html, body, ul, ol {
      margin: 0;
      padding: 0;
    }
    body {
      font: 100% Helvetica, sans-serif;
      background-color: #efefef;
    }

Si no se da ninguna de las anteriores circunstancias, y la extensión del archivo importado es .scss o .sass, entonces se importan directamente los contenidos de ese archivo. Si no se indica la extensión, Sass tratará de buscar un archivo con ese nombre y con las extensiones .scss o .sass. Ejemplos:

|      Regla @	               	| Resultado			|
|-------------------------------|-------------------------------|
| @import "foo.scss";		| Se importa el archivo foo.scss|
| @import "foo";		| Se importa el archivo foo.scss|
| @import "foo.css";		| @import "foo.css"; 		|
| @import "foo" screen;		| @import "foo" screen; 	|
| @import "http://foo.com/bar";	| @import "http://foo.com/bar"; |
| @import url(foo);		| @import url(foo); 		|


También es posible importar varios archivos con una sola regla @import. Ejemplo:

@import "rounded-corners", "text-shadow";
Esta regla importaría tanto el archivo rounded-corners como el archivo text-shadow.

El nombre del archivo importado también se puede establecer con la interpolación #{ }, pero con ciertas restricciones. No se puede importar dinámicamente un archivo Sass en base al nombre de una variable, pero sí que se puede importar de esta manera un archivo CSS. De forma que la interpolación solamente funciona en la práctica cuando se utiliza url(). Ejemplo:

$family: unquote("Droid+Sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");
El código Sass anterior se compila de la siguiente manera:

@import url("http://fonts.googleapis.com/css?family=Droid+Sans");

### 11 Mixins
Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes. Here's an example for border-radius.

    =border-radius($radius)
      -webkit-border-radius: $radius
      -moz-border-radius:    $radius
      -ms-border-radius:     $radius
      border-radius:         $radius
      
    .box
      +border-radius(10px)
  

Para crear un mixin utiliza la directiva  @mixin y darle un nombre. 
Hemos llamado a nuestra mixin border-radius .
También estamos usando la variable $radiusdentro de los paréntesis para que podamos pasar en un radio de lo que queramos.
Después de crear tu mixin , puede utilizarlo como una declaración CSS comenzando con @include seguido del nombre del mixin . 
Cuando se genera el CSS que va a tener este aspecto 

    .box {
      -webkit-border-radius: 10px;
      -moz-border-radius: 10px;
      -ms-border-radius: 10px;
      border-radius: 10px;
    }
    
### 12 Extend/Inheritance

Esta es una de las características más útiles de Sass . 
Usando extend le permite compartir un conjunto de propiedades CSS de un selector a otro .
En nuestro ejemplo vamos a crear una simple serie de mensajes de errores, advertencias y éxitos.

    .message
      border: 1px solid #ccc
      padding: 10px
      color: #333
      
    .success
      @extend .message
      border-color: green
      
    .error
      @extend .message
      border-color: red
      
    .warning
      @extend .message
      border-color: yellow


El código anterior permitir Extender/Heredar las propiedades CSS en .Message y aplicarlos a .success , .Error , y .warning.
La magia sucede con el CSS generado, esto ayuda a evitar tener que escribir varios nombres de clase en los elementos HTML . Esto es lo que parece:

    .message, .success, .error, .warning {
      border: 1px solid #cccccc;
      padding: 10px;
      color: #333;
    }
      
    .success {
      border-color: green;
    }
      
    .error {
      border-color: red;
    }
      
    .warning {
      border-color: yellow;
    }


### 13 Operators
Utilizar las matemáticas en CSS puede resultar muy útil. Sass tiene algunos operadores matemáticos estándar como +, - , *, / y% .
En nuestro ejemplo vamos a hacer un poco de matemática simple para calcular anchos para un lado y artículo.

    .container
      width: 100%
      
    article[role="main"]
      float: left
      width: 600px / 960px * 100%
      
    aside[role="complimentary"]
      float: right
      width: 300px / 960px * 100%

Hemos creado una rejills (grid) simple , basado en 960px .
Las operaciones en Sass no deja hacer algo así como los valores de píxel y las convierten a porcentajes sin mucha molestia .
El CSS generada se verá así :

    .container {
      width: 100%;
    }
      
    article[role="main"] {
      float: left;
      width: 62.5%;
    }
      
    aside[role="complimentary"] {
      float: right;
      width: 31.25%;
    }



