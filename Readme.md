<header style="background-color: rgba(33,148,214,.5)">
<img src="imgs/logos/logo-default.png"></img>
</header>
# Tecnogeo SASS framework

### Configuraci&oacute;n:

#### style.scss
Configura primeramente el archivo `scss/style.scss` con los archivos que quieres incluir.
Si no quieres incluir el archivo _fuentes.scss porque no los vas a usar o cualquiero otro
archivo por cualquier otra raz&oacute;n, comenta esa l&iacute;nea para que no compile CSS de m&aacute;s y
optimizar en peso.

#### variables.scss
Pasa a configurar las variables y diferentes opciones de la atm&oacute;sfera de dise&ntilde;o,
nos vamos a `variables.scss` donde podremos configurar colores, fuentes, tama&ntilde;os, 
etc...

### Breakpoints 
Los breakpoints los he colocado en EM en vez de pixels para que el dise&ntilde;o no se 
vea afectado por acciones como el ZOOM. Para m&aacute;s info leer a 
[Chris Coyer](http://css-tricks.com/why-ems/) y a [Lyza Gardner](http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/) con argumentos al respecto.

```scss
$bp1 : 30em;      // 480px
$bp2 : 37.5em;    // 600px
$bp3 : 48em;      // 768px
$bp4 : 56.25em;   // 900px
$bp5 : 68.75em;   // 1100px
```

### Nomenclatura
La convenci&oacute;n de nombre sigue este patr&oacute;n:

* **Componentes**: un módulo de página que tiene un cierto propósito y es un wrapper para sus hijos, por ejemplo, un modal o un slider pueden ser componentes.
* **Nested Elements/hijos**: Partes de un componente, a veces similares entre componentes.
* **Variantes/modificadores**: Un componente que contiene elementos que lo modifican de una cierta forma.
* **Estados**: El estado de un componente o de un hijo es modificado por la interacción del usuario, por ejemplo un boton desabilitado.


##### COMPONENTES

```css
    .bloque{}
    .bloque-nombre{}
    .bloque-partenombre-partenombre{}
```

* **'.bloque'** representa el primer nivel de una abstracci&oacute;n o componente.
* **'.bloque-nombre'** representa el primer nivel de una abstracci&oacute;n o componente. 
* **'.bloque-partenombre-partenombre'** representa el primer nivel de una abstracci&oacute;n o componente. Varios guiones pueden formar un nombre largo.


##### VARIANTES/MODIFICADORES

```css
    .bloque{}
    .bloque--modificador1{}
    .bloque--modificador2{}
```

Por ejemplo: 

```css
    .persona{}
    .persona--mujer{}
    .persona--hombre{}

```

* **'.persona'** representa el primer nivel de una abstracci&oacute;n o componente.
* **'.persona--mujer'** representa una variante/modificaci&oacute;n de un elemento de primer nivel de una abstracci&oacute;n o componente. 
* **'.persona--hombre'** representa otra variante/modificaci&oacute;n de un elemento de primer nivel de una abstracci&oacute;n o componente. 


##### MODIFICADORES Y INDICADORES DE ESTADO

Esto es una variante realmente. 

```css
    .bloque.estado{}
    .bloque-nombre.estado-nombre{}
    .bloque.js-estado{}  / ** Para comportamiento aplicado via JS ** /
```

Por ejemplo:

```css
    .bloque.is-active{}
    .bloque-name.has-children{}
    .bloque.js-selected{}
```

##### HIJOS (ELEMENTOS ANIDADOS)

```css
    .bloque{}
    .bloque__elemento{}
   
```

Por ejemplo: 

```css
    .component__link{}
    .component-name__link-element{}
  
```

* **'.bloque__elemento'** representa un descendente de '.bloque' que se ayuda de 
'.bloque' como un conjunto.
* **'.bloque--modificador'** representa un estado diferente de '.bloque'.

Una **analog&iacute;a** del funcionamiento de las clases BEM ser&iacute;a:

```css
    .persona{}
    .persona--mujer{}
        .persona--mujer__mano{}
        .persona--mujer__mano--izquierda{}
        .persona--mujer__mano--derecha{}

    .persona--hombre{}
        .persona--hombre__mano{}
        .persona--hombre__mano--izquierda{}
        .persona--hombre__mano--derecha{}

    .wrapper{}
        .container{}
            .header{}
                .header__img{}
                .header__img--general{}
                .header__img--nav{}
            .content{}
            ...
```

Otra opci&oacute;n de implementaci&oacute;n:


```css
    .persona{}
    .persona--mujer{}
    .persona--mujer .persona__mano{}
    .persona--mujer .persona__mano .persona__mano--izquierda{}

```
Por ejemplo, un pie de p&aacute;gina podria ser como este:

```css
    .Pie {
        font-size: 7pt;
        width: 100%;
        color: #404040;
        font-family: Arial, Helvetica, Sans-Serif;
        height: 22px;
        text-align: center;
    }

    .Pie A {
        color: #404040;
        text-decoration: none;
    }

    .Pie A:hover {
        color: #404040;
        text-decoration: underline;
    }

    .Pie A:active {
        color: #404040;
        text-decoration: none;
    }

 
```
o tambi&eacute;n:

```css
    .Pie {
        font-size: 7pt;
        width: 100%;
        color: #404040;
        font-family: Arial, Helvetica, Sans-Serif;
        height: 22px;
        text-align: center;
    
        &; A {
            text-decoration: none;
        }

        &; A:hover {
            text-decoration: underline;
        }

        &; A:active {
            text-decoration: none;
        }
    }

 
```





Para m&aacute;s info pod&eacute;is leer esta traducci&oacute;n de la [gu&iacute;a de CSS](https://github.com/Wakkos/CSS-Guidelines) de [Harry Roberts](https://twitter.com/csswizardry) 
a la cual me he ajustado en su mayor&iacute;a para crear este framework.

Tambi&eacute;n tenemos espacio entre secciones para que sea f&aacute;cil de ubicar al ver el 
archivo compilado `style.css`.


### Organizaci&oacute;n

La **estructura principal** de directorios del framework es la siguiente:

```
->FrameworkCss
    ->css       (directorio con css principal a llamar en la p&aacute;gina web)
    ->data      (directorio con datos de la web)
    ->docs      (directorio con todo tipo de documentaci&oacute;n)
    ->fonts     (directorio de fuentes de todo el framework)
    ->imgs      (directorio con todas las im&aacute;genes del framework)
    ->js        (directorio con todos los scripts del framework)
    ->patrones  (directorio donde se genera la guia de estilos)
    ->scss      (directorio sass donde estar todo el material y estilos para compilar)
    ->vendor    (directorio con frameworks de 3rd party)

```
```

```
Seguidamente se muestra toda la estructura interna de los directorios principales. Los archivos de **SCSS** est&aacute;n todos dentro de la carpeta `scss` y distribuidos 
de la siguiente manera:

````

->FrameworkCss
    ->css (directorio con css principal a llamar en la pàgina web)
        --debug.css
        --it-ie9.css
        --style.css

    ->data (directorio con datos de la web)

    ->docs (directorio con todo tipo de documentaci&oacute;n)
        --docsdoc
        --docspdf
        --docsppt
        --docstxt
        --docsxls
        
        readme.html  (se genera autom&aacute;ticament con prepros)
        readme.md    (fichero a editar para describir este directorio y su contenido)

    ->fonts (directorio de fuentes de todo el framework)
        readme.html  (se genera autom&aacute;ticament con prepros)
        readme.md    (fichero a editar para describir este directorio y su contenido)

    ->imgs (directorio con todas las im&aacute;genes del framework)
        --bg            (directorio de imagenes de background)
        --icons         (directorio de iconos)
        --icons16x16    (directorio de iconos de tama&ntilde;o 16x16)
        --icons32x32    (directorio de iconos de tama&ntilde;o 32x32)
        --logos         (directorio de logos)


    ->js (directorio con todos los scripts del framework)
        --min           (directorio con los js minificados)

    ->patrones (directorio donde se genera la guia de estilos)
        atoms.html  (se genera autom&aacute;ticament con prepros)
        atoms.md    (fichero a editar los tipos de atomos principales de la guia)
        index.html  (**p&aacute;gina web de la guia principal!!**)

        --css           (directorio principal donde se genera el css principal de la guia)
        --imgs          (directorio con todas las im&aacute;genes de la guia)
                --bg            (directorio de imagenes de background)
                --icons         (directorio de iconos)
                --icons16x16    (directorio de iconos de tama&ntilde;o 16x16)
                --icons32x32    (directorio de iconos de tama&ntilde;o 32x32)
                --logos         (directorio de logos)     
        --scss          (directorio sass donde estar todo el material y estilos para compilar de la guia)
                --_patron.scss  (fichero principal para crear elementos propios de la guia)
                --style.scss    (fichero principal que realiza todos los imports de la guia)

           
    ->scss (directorio sass donde estar todo el material y estilos para compilar)
        debug.scss   (fichero para ayuda en fallos sint&aacute;cticos)
        It-ie9.scss  (fichero de imports de scss para cargar ficheros sass compatibles con ie9)
        style.scss   (fichero de imports principal del framework con todos los sass)
 
        --base
                     _reset.scss
                     _normalize.scss
                     _fuentes.scss
                     _tipografia.scss
                     _variables.scss    ( contiene todas las variables generales del framework )
       --componentes
                     _botones.scss
                     _elementos.scss
                     _flex.scss
                     _formularios.scss
                     _links.scss      
                     _navegacion.scss
                     _paginacion.scss
                     _placeholders.scss
                     _tablas.scss
                     _texturas.scss

        --doc 
                    _contenido.scss
        --functions
                    _convertions.scss
                    _functions.scss
                    _tint-shade.scss
        --mixins
                    _mixins.scss  ( contiene todos los imports de los mixins)
        --layout
                    --Template1
                    --Template2
                    --Template3
                    _2x.scss
                    _breakpoints.scss
                    _content-home.scss
                    _footer.scss
                    _formularios.scss
                    _grid.scss
                    _header.scss
                    _sidebar.scss
        --layout
                    _inicio.scss
                    _sitio.scss
        --themes
        --vendors   

    ->vendor (directorio con ficheros sass de 3rd party)
                        

        
```        
``` 

```
El archivo `contenido.scss` se compila al principio del `style.css` para dar una 
gu&iacute;a de donde tenemos nuestros elementos y su nombre, gracias a los comentarios 
BEM la búsqueda `cmd/ctrl + f`en SublimeText que empiece por $NOMBREDESECCION 
nos ayudar&aacute; mucho a encontrar el contenido.

A su vez est&aacute;n todas las secciones separadas unas de las otras para ubicar r&aacute;pidamente
 cuando echamos un vistazo.

El archivo `_debug.scss` viene comentado, pero lo puedes incluir para tener una 
peque&ntilde;a gu&iacute;a de la sem&aacute;ntica de tu documento html.

El archivo `lt-ie9.scss` incluye un fallback para todo lo que incluimos en los
 mediaqueries con la clase `.ie8-sucks`. Si os da corte con vuestro cliente, 
 pod&eacute;is cambiar la clase en el archivo `_variables.scss`.

### Prepros/Codekit
Ir&eacute; adapt&aacute;ndolo a Prepros/Codekit pero sin que afecte a los que no lo usan. De momento si 
usas Codekit, incluyo el archivo `config.codekit`. Todos los `.scss`son compilados 
en la carpeta `css`.

## Patrones
Siempre necesito una gu&iacute;a de estilos o de patrones para hacerme una idea de la 
atm&oacute;sfera de dise&ntilde;o de la web. Para esto tengo la carpeta `patrones`donde tengo 
el `index.html` que me da un peque&ntilde;o resumen de los elementos de la web y se ajusta
a la configuraci&oacute;n de nuestro CSS.

Me gustar&iacute;a poner c&oacute;digo en cada elemento para as&iacute; hacer que sea funcional no solo
al dise&ntilde;ador sino al frontend, pero ese trabajo va a tener que esperar.


## Tip1
_Modulariza_ **todo** lo que puedas, el archivo `style.scss` 
es para meter archivos. Crea m&oacute;dulos, divide tu CSS en tantos archivos como puedas; 
el CSS del header en `header.scss`, `content-home.scss`, `footer.scss`, etc...


## Tip2
Se deberia intentar seguir esta convenci&oacute;n de nombres o algo parecido
http://www.apppie.org/pages/approach/naming.html