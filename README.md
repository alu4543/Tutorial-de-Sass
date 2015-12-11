# Sistemas y Tecnologías Web
## Tutorial con ejemplos básicos de Sass
### 1. introducción
Sass acrónimo de (Syntactically Awesome StyleSheets)
Es un preprocesador de CSS que añade características muy potentes y elegantes.
Sass incluye las siguientes características:
* 100% compatible con CSS3.
* Permite el uso de variables, anidamiento de estilos, importación de hojas de estilos y mixins, gracias a la librería Compass.
* Incluye numerosas funciones para manipular con facilidad colores y otros valores.
* Permite el uso de elementos básicos de programación como las directivas de control y las librerías.
* Genera archivos CSS bien formateados y permite configurar su formato.


### 2. Pre-instalación
Para usar Sass es necesario tener instalado Ruby. La instalación es un proceso bastante sencillo.

#### 2.1 Linux
Si estás usando una distribución de Linux, Puedes instalar Rubi a través del gestor de paquetes apt , rbenv o RVM .

      $ sudo apt-get install ruby-full rubygems1.8

#### 2.2 Windows
La manera más sencilla de instalar Rubi en  Windows es utilizar **[Ruby Installer.](http://rubyinstaller.org )**  
El programa de instalación también instalará Ruby command line powershel que le permitirá utilizar librarias de Ruby.

#### 2.3 Mac
¡Felicidades!
Ruby viene pre-instalado.

### 3. instalación de Sass
Aquí está la forma más sencilla para empezar a utilizar Sass mediante el uso de la línea de comandos :
Rubí utiliza gemas para gestionar sus diversos paquetes de código como Sass.

#### 3.1 Comandos para la instalación

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

### 4. Complación
El codigo escrito en Sass se compila mas adelante para obtener el codigo CSS para que los navegadores lo puedan leer.

#### 4.1 Desde consola
Para ejecutar Sass desde la línea de comandos, sólo tiene que ejecutar:

      $ sass main.sass style.css

#### 4.2 Vigilar (Watch)
También puede decirle a Sass que vegile el archivo Sass y actualizar el CSS cada vez que el archivo Sass cambie :

      $ sass --watch main.sass:style.css

#### 4.3 Vigilar un directorio
Pero si usted tienes un directorio con muchos archivos Sass, también puede decirle Sass para ver todo el directorio :

      $ sass --watch app/sass:public/stylesheets

### 5. Conversión y compatibilidad de sintaxis
Una de las ventajas de Sass es que los archivos creados con una sintaxis pueden importar cualquier archivo creado con la otra sintaxis.
Además, disponemos de una utilidad para la línea de comandos que te permite convertir una sintaxis en otra:

#### 5.1 Convierte un archivo Sass en SCSS

      $ sass-convert main.sass main.scss

#### 5.2 Convierte un archivo SCSS en Sass

      $ sass-convert main.scss main.sass

### 6. Variables
las variables puede almacenar cosas como colores ,fuente o cualquier valor CSS que querremos ruetilizar a lo largo de la hoja de estilo.
Sass usa el símbolo $ para las variables, a continuación un ejemplo :
#### 6.1 Ejemplo

      $fuente:    Helvetica, sans-serif
      $rojo: #FF0000
      body
            font: 100% $fuente
            color: $rojo

Cuando se procesa el Sass ,toma las variables que definimos $fuente y $rojo y genera la salidas CSS con nuestros valores de las variables puestas en la CSS.
Esto puede ser muy útil cuando se trabaja con los colores de una marca y los mantiene constante a través del sitio.

CSS Generado

      body {
            font: 100% Helvetica, sans-serif;
            color: #FF0000;
      }

### 8. Nesting (Anidamiento)
#### 8.1 ¿Que es Anidamiento?
Notamos que al escribir HTML tiene una jerarquía anidada visual y clara . CSS, por otra parte, no lo hace .
Sass le permitirá a CSS que siga la misma jerarquía visual de su HTML.
#### 8.2 Advertencia
En general se considera una mala práctica crear reglas excesivamente anidadas, podría resultar difícil de mantener, con esto en mente, a continuación un ejemplo :

##### 8.2.2 Ejemplo

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

los ul , li , y a  se anidan en el interior del selector de navegación .
Para organizar tu CSS y hacerlo más legible no veo otra forma mejor.
Al generar el CSS obtendrás algo como esto:

CSS Generado

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

### 9. Partials
#### 9.1 ¿que es un parcial?
Un parcial es simplemente un archivo Sass llamado con un subrayado inicial algo así como _partial.sass .
El subrayado permite a Sass saber que el archivo es un archivo solamente parcial y que no debe ser generado en un archivo CSS. Los parciales Sass se utilizan con la directiva import .
#### 9.2 ¿Para que sirve?
##### 9.2.1 Fragmentación de código
Se pueden crear archivos parciales que contienen pequeños fragmentos de CSS que se pueden incluir en otros archivos Sass.
##### 9.2.3 CSS modularizado.
Esta es una buena practica para modularizar el CSS y facilita que nuestras hojas de estilos séan más fáciles de mantener.

### 10. Import

CSS tiene una opción de importación que le permite dividir su hoja de estilo en porciones más pequeñas y fáciles de mantener.
El único inconveniente es que cada vez que se utilice @import en CSS crea otra petición HTTP .
Sass construye en la parte superior de la CSS actual @import pero en lugar de construir una solicitud HTTP, Sass tomará el archivo que desea importar y combinarlo con el archivo que está importando para que pueda servir a un solo archivo CSS para el navegador web.

Supongamos que tenemos un par de archivos Sass , _reset.scss , base.scss. y Queremos importar _reset.scss hacia base.scss.

#### 10.1 Ejemplo

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

Está usando import 'reset' en el archivo base.scss. y no es necesario indicarle la extención extensión .scss  de archivo, lo importa y incluye su contenido en la generación del CSS final.

CSS Generado

    html, body, ul, ol {
      margin: 0;
      padding: 0;
    }
    body {
      font: 100% Helvetica, sans-serif;
      background-color: #efefef;
    }
Sass es inteligente, si no se indica la extensión, Sass tratará de buscar un archivo con ese nombre y con las extensiones .scss o .sass.

      |      Regla @	               	| Resultado			            |
      |-----------------------------------|-----------------------------------|
      | @import "foo.scss";		      | Se importa el archivo foo.scss    |
      | @import "foo";		            | Se importa el archivo foo.scss    |
      | @import "foo.css";		      | Se importa el archivo foo.css     |
      | @import "http://foo.com/bar";	| Se importa http://foo.com/bar     |
      | @import url(foo);		      | Se importa lo que hay en la url   |


También es posible importar varios archivos con una sola regla @import. Ejemplo:

      @import "rounded-corners", "text-shadow";

Esta regla importaría tanto el archivo rounded-corners como el archivo text-shadow.

El nombre del archivo importado también se puede establecer con la interpolación #{ }, pero con ciertas restricciones.
      No se puede importar dinámicamente un archivo Sass en base al nombre de una variable, pero sí que se puede importar de esta manera un archivo CSS.
      De forma que la interpolación solamente funciona en la práctica cuando se utiliza url(). Ejemplo:

      $family: unquote("Droid+Sans");
      @import url("http://fonts.googleapis.com/css?family=#{$family}");

El código Sass anterior se compila de la siguiente manera:

      @import url("http://fonts.googleapis.com/css?family=Droid+Sans");

### 11 Mixins
#### 11.1 Utilidad
Algunas cosas en CSS son un poco tedioso de escribir, especialmente con CSS3 y los muchos prefijos de los diferentes navegadores.
Un mixin permite hacer grupos de declaraciones CSS que puedo ruetilizar un todo el sitio.

#### 11.2 Sintaxis
Para crear un mixin utiliza la directiva  @mixin y darle un nombre.
Después de crear nuestro mixin podemos utilizarlo como una declaración CSS comenzando con @include seguido del nombre del mixin.
Un buen uso de un mixin es para prefijos de proveedores.
Veamos un ejemplo:

    @mixin border-radius($radius) {
      -webkit-border-radius: $radius;
         -moz-border-radius: $radius;
          -ms-border-radius: $radius;
              border-radius: $radius;
    }

    .box { @include border-radius(10px); }

Cuando se genera el CSS que va a tener este aspecto

    .box {
      -webkit-border-radius: 10px;
      -moz-border-radius: 10px;
      -ms-border-radius: 10px;
      border-radius: 10px;
    }

#### 11.3 Argumentos
Los argumentos de los mixins pueden estar formados por cualquier expresión Sass. Estos argumentos están disponibles en el interior del mixin en forma de variables.
Cuando se define un mixin, los argumentos se definen como una serie de variables separadas por comas, y todo ello encerrado entre paréntesis. Después, cuando se utiliza un mixin deben pasarse los valores de los argumentos en ese mismo orden.
Otro Ejemplo:

      @mixin mi-border($color, $width) {
        border: {
          color: $color;
          width: $width;
          style: dashed;
        }
      }

      p { @include mi-border(blue, 1in); }
El código Sass anterior se compila de la siguiente manera:

      p {
        border-color: blue;
        border-width: 1in;
        border-style: dashed;
      }
##### 11.3.1 Argumentos con Valores por defecto
Los mixins también pueden especificar valores por defecto para sus argumentos. De esta manera, si al llamar a un mixin no se pasa el valor de ese argumento, se utiliza en su lugar el valor por defecto. Ejemplo:

      @mixin mi-border($color, $width: 1in) {
        border: {
          color: $color;
          width: $width;
          style: dashed;
        }
      }
      p { @include mi-border(blue); }
      h1 { @include mi-border(blue, 2in); }
El código Sass anterior se compila de la siguiente manera:

      p {
        border-color: blue;
        border-width: 1in;
        border-style: dashed;
      }

      h1 {
        border-color: blue;
        border-width: 2in;
        border-style: dashed;
      }

### 12. Extend/Herencia
Esta es una de las características más útiles de Sass .
Usando extend le permite compartir un conjunto de propiedades CSS de un selector a otro .
En nuestro ejemplo vamos a crear una simple serie de message de errores, advertencias y éxitos.

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


### 13. Operadores
Utilizar las matemáticas en CSS puede resultar muy útil. Sass tiene algunos operadores matemáticos estándar como +, - , *, / y% .
En nuestro ejemplo vamos a hacer un poco de matemática simple para calcular anchos para un lado y artículo.

#### 13.1 Ejemplo

    .container
      width: 100%

    article[role="main"]
      float: left
      width: 600px / 960px * 100%

    aside[role="complimentary"]
      float: right
      width: 300px / 960px * 100%

Hemos creado un grid simple , basado en 960px .
Las operaciones en Sass nos deja hacer algo así como los valores de píxel y las convierten a porcentajes sin mucha molestia .

#### 13.2 CSS Generado:

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

### 14. Bibliografía
http://sass-lang.com/


#### 15.Links de la práctica:
* **[Despliegue](http://alu4543.github.io/Tutorial-de-Sass/)**
* **[GitHub](https://github.com/alu4543/Tutorial-de-Sass)**
* **[web de la asignatura](http://alu4543.github.io/)**
