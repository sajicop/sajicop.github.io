#  Tema 4. HTML i CSS

## 4.1 Introducció a HTML

HTML (HyperText Markup Language) és un llenguatge de marques que permet visualitzar documents a la Web.

Les etiquetes utilitzades a HTML, com per exemple "paràgraf" (&lt;p&lt;) o "taula" (&lt;table&gt;) no es mostren en el navegador, sino que indiquen com mostrar la informació.

L'estructura de HTML és semblant a XML: etiquetes, atributs, element arrel, etc... però el nom dels elements està establert, no ens els podem inventar. És a dir, HTML no és un metallenguatge i hem d'aprendre les etiquetes ja predefinides. 

HTML5 es va llançar el 2014 i és la última versió del llenguatge.

Dintre d’un document HTML podem trobar 3 llenguatges diferents:

![Llenguatges Web](assets/img/html-css-js.png "Llenguatges Web")

Javascript (JS) és un llenguatge de programació i permet la creació de pàgines web interactives.

Estructura d’una pàgina HTML5:

```html
  <!DOCTYPE html>
  <html lang=”ES”>
      <head>
          <meta charset=”utf-8”>
          <meta name=”viewport” content="width=device-width, initial-
          scale=1.0">
          <title></title>
          <!-- scripts, css, meta -->
      </head>
      <body>
          <h1>Això és un <b>titular</b> en HTML</h1>
          <p>Aquest és el primer paràgraf.</p>
      </body>
  </html>
```

La primera linea indica que el document és un document HTML5. A continuació hem d’escriure l’element arrel (__html__) especificant l’idioma amb l’atribut lang.

L’etiqueta __head__ permet especificar algunes metadades adicionals sobre la pàgina web. Els elements que apareixen dintre de l’element __head__ no surten al navegador. Dintre podem especificar el joc de caràcters que farem servir, el títol de la web (surt a la barra del navegador) i enllaços a diferents fitxers, com scripts, estils css, etc.

L’etiqueta __body__ representa el contingut de la pàgina i tot el que afegim en aquesta part sortirà al navegador.

## 4.2. Demo

Afegir snippet a Visual Studio Code
https://code.visualstudio.com/docs/editor/emmet


Instalar extensión Live Server per iniciar el navegador web des del codi font:

Per veure el resultat:


Més informació:&lt:

[Element Meta (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta)

[HTML5 template complet](https://www.sitepoint.com/a-basic-html5-template/)


## 4.3. Elements bàsics de formateig

Existeixen molts elements HTML per donar format al nostre texte. Alguns dels més utilitzats són:

* Capceleres: &lt;h1&gt;&lt;/h1&gt;
              &lt;h2&gt;&lt;/h2&gt;
               ...
              &lt;h6&gt;&lt;/h6&gt;
* Paràgraf: &lt;p&gt;&lt;/p&gt;
* Texte preformatejat: &lt;pre&gt;&lt;/pre&gt;
* Forçar salt de línia o espai: &lt;/br&gt; i &nbsp;
* Línia horizontal: &lt;hr&gt;
* Efectes de texte (negreta, èmfasi, subratllat, ratllar): &lt;strong&gt;, &lt;em&gt;, &lt;ins&gt;, &lt;del&gt;
* Resaltat de texte, subíndex, superíndex: &lt;mark&gt;&lt;sub&gt;&lt;sup&gt; H2O H&lt;sub>2&lt;/sub&gt;O



El resultat dels elements bàsics seria:
<p></p>

<h1>Capcelera H1</h1>
<h2>Capcelera H2</h2>
<h3>Capcelera H3</h3>
<h4>Capcelera H4</h4>
<h5>Capcelera H5</h5>
<h6>Capcelera H6</h6>

<p></p>

<p>Això es un paràgraf a HTML</p>

<p></p>

<pre>
Tu corazón, ya terciopelo ajado,
llama a un campo de almendras espumosas
mi avariciosa voz de enamorado.
</pre>

<p></p>

Alguns efectes de texte bàsics com <strong>negreta</strong>, <em>èmfasi</em>, <ins>subratllat</ins> o <del>ratllar</del>, s'aconsegueixen amb les etiquetes strong, em, ins o del.

Podem <mark>resaltar el texte</mark> i crear subíndex i superíndex, com a H2O => H<sub>2</sub>O


Més informació:

[Introduction to HTML (Mozilla.org)](https://developer.mozilla.org/es/docs/Learn/HTML/Introduction_to_HTML/)

Capítols:
* HTML_text_fundamentals
* Advanced_text_formatting

## 4.4. Enllaços

Els enllaços són un dels elements més importants, doncs fan que des de la web sigui navegable, és a dir, es puguin visitar altres webs clicant sobre enllaços, L’element &lt;a&lt; (ancla o “anchor”) fa que la web sigui navegable. Podem fer un enllaç a una URL externa, a un altre lloc de la mateixa pàgina o a una adreça de correu electrònic.

Enllaços a una url externa:
```html
<a href=”http://www.exemple.org”>texte de l’enllaç</a>
```

També podem crear un enllaç dins la mateixa pàgina (per índex, referències,etc.).
```html
<h2 id="Mailing_address">Mailing address</h2>
Escriu-nos a <a href="contacts.html#Mailing_address">mailing address</a>
<a href=”#Mailing_address></a>
```

Inclús podem enllaçar a una adreça de correu (s’obre el gestor de correu per defecte):
```html
<a href="mailto:nowhere@mozilla.org">Envia email a cap lloc</a>
```

Atributs més comuns:

* href: HyperText Reference
* title: mostra una descripció quan es pasa el ratolí per sobre
* target: “__blank” obre l’enllaç en una nova finestra



Més info:

[Creating HyperLinks](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)


## 4.5. Imatges

Un altre element molt important permet mostrar recursos gràfics a la web.

Sintaxi:
```html
<img src=”images/dinosaur.jpg”
     alt="The head and torso of a dinosaur skeleton; it has a large head with long sharp teeth"
     width=”200” height=”400”
     title="A T-Rex on display in the Manchester Museum">
```

La font pot ser una subcarpeta del servidor o una URL:
```html
<img src="/images/stickman.gif" alt="Stickman" width="24" height="39">
<img src="https://www.w3schools.com/images/lamp.jpg" alt="Lamp" width="32" height="32">
```

Imatge amb enllaç
```html
<a href="https://www.w3schools.com">
<img src="w3html.gif" alt="W3Schools.com" width="100" height="132">
</a>
```

L'element a admet els següents formats d’imatge:
* JPG
* PNG
* GIF
* BMP
* SVG (vectorial, basat en XML)

## 4.6. Llistes

Les llistes ens permeten mostrar elements amb vinyetes per formar una llista d’elements. Les llistes poden ser ordenades, desordenades i de definició. 
Unordered List

```html
  <h3>Llista de la compra:</h3>
  <ul>
    <li>Patates</li>
    <li>Vi</li>
    <li>Pollastre</li>
  </ul>
  Ordered List
  <h3>Grups favorits:</h3>
  <ol>
    <li>Led Zeppelin</li>
    <li>Metallica</li>
    <li>Iron Maiden</li>
  </ol>
  Definition List
  Sintaxi:
  <dl>
    <dd>Definició-1</dd>
    <dt>Terme-1</dt>
    <dd>Definició-2</dd>
    <dt>Terme-2</dt>
  </dl>
```

<h3>Llista de la compra:</h3>
<ul>
<li>Patates</li>
<li>Vi</li>
<li>Pollastre</li>
</ul>
Ordered List
<h3>Grups favorits:</h3>
<ol>
<li>Led Zeppelin</li>
<li>Metallica</li>
<li>Iron Maiden</li>
</ol>
Definition List
Sintaxi:
<dl>
<dd>Definició</dd>
<dt>Terme</dt>
...
</dl>

Exemple de llista de definicions:

```html
<p>Termes informàtics:</p>
<dl>
  <dt>Cookie</dt>
  <dd>Un pequeño archivo de texto enviado por un sitio web
  visitado. Permite reconocer al usuario y personalizar
  la web.</dd>
  <dt>Spam</dt>
  <dd>Mensajes de correo no deseados enviados masivamente y
  generalmente por motivos comerciales.</dd>
  <dt>CAPTCHA</dt>
  <dd>Las comprobaciones CAPTCHA permiten verificar que el
  usuario de una web es un humano y no un bot o un
  proceso automatizado.</dd>
</dl>
```

<p>Termes informàtics:</p>
<dl>
<dt>Cookie</dt>
<dd>Un pequeño archivo de texto enviado por un sitio web
visitado. Permite reconocer al usuario y personalizar
la web.</dd>
<dt>Spam</dt>
<dd>Mensajes de correo no deseados enviados masivamente y
generalmente por motivos comerciales.</dd>
<dt>CAPTCHA</dt>
<dd>Las comprobaciones CAPTCHA permiten verificar que el
usuario de una web es un humano y no un bot o un
proceso automatizado.</dd>
</dl>


L’estil de les vinyetes de les llistes es pot canviar amb CSS!

```css
  ul {
  list-style-type: none;
  }
```

## 4.7. Taules. Estructura bàsica.

Les taules ens permeten mostrar la informació en files I columnes. Fa uns anys es feia servir per posicionar el elements a la finestra del navegador. Actualment hi ha altres tècniques amb CSS per a posicionament d’elements.

Un exemple bàsic:

```html
  <table>
    <thead>
      <tr>
        <th>capcelera1</th>
      <th>capcelera2</th>
      </tr>
    </thead>
    <tbody>
      <tr> <!-- table row -->
      <td>fila1 col1</td>
      <td>fila1 col2</td>
      </tr>
    </tbody>
  </table>
```

Sortida:

  <table>
    <thead>
      <tr>
        <th>capcelera1</th>
      <th>capcelera2</th>
      </tr>
    </thead>
    <tbody>
      <tr> <!-- table row -->
      <td>fila1 col1</td>
      <td>fila1 col2</td>
      </tr>
    </tbody>
  </table>


L’element __table__ permet definir la taula i establir alguns atributs bàsics com border-width. Podem donar estil a una taula (canviar el color de la capcelera,
alternar color files, etc.) amb les fulles d’estil CSS, que veurem més endavant. L’element __thead__ ens permet especificar els títols de les columnes i __th__ és
equivalent a __td__, és a dir conté les dades de la cel.la (table data). La resta de files s’han d’incloure dintre de l’etiqueta __tbody__.
L’element __tr__ obre una nova línia i dintre hi podem afegir tants elements __td__ com volguem.
Per últim també tenim l’etiqueta __tfooter__ per afegir un peu de taula, per exemple per sumaritzar alguna de les columnes.

## 4.8. Formularis

Els formularis són un dels elements HTML més complexos. Permeten recollir dades de l’usuari amb la incorporació de controls (input, radio button, dropdown, botons,
etc. Amb l’ajuda d’un llenguatge de servidor (PHP, NodeJS) podem guardar-ho en una base de dades. L’esquema bàsic per a un formulari seria:

```html
  <form action=”gestio-form.php” method=”post”>
  <label for=”name”>Nom</label>
  <input type=”text” id=”name”>
  ...
  <input type=””>
  <button type=”submit”>Submit</button>
  </form>
```

Els tipus d’elements que podem incloure en un formulari són:



|Element                                                           | Significat                                                       |
|------------------------------------------------------------------|-----------------------------------------------------------------|
| &lt;label for=”id_input”&gt;Texte&lt;/label&gt;                              | Etiqueta per a camp texte                                       |
| &lt;input type=”text”&gt;                                              | Camp de texte                                                   |
| &lt;input type=”email”&gt;                                             | Valida email: usuari@domini                                     |
| &lt;textarea&gt;...&lt;/textarea&gt;                                         | Área de texte major que input                                   |
| &lt;button type=”submit”&gt;&lt;/button&gt;                                  | Envía el formulari al servidor                                  |  
| &lt;fieldset&gt;&lt;legend&gt;&lt;/legend&gt;&lt;/fieldset&gt;                           | Dibuixa un marc amb títol dels camps                            |
| &lt;input type=”radio”&gt;                                             | Radio button                                                    |
| &lt;input type=”checkbox”&gt;                                          | Checkbox                                                        |
| &lt;input type=”date”&gt;                                              | Control amb selector de data                                    |
| &lt;input type=”file”&gt;                                              | Control amb selector de arxius                                  |
| &lt;select&gt;&lt;option selected=”selected”&gt;O1&lt;/option&gt; &lt;option&gt;On&lt;/option&gt;&lt;/select&gt;  | Desplegable amb opcions predefinides. Atribut selected opcional.
|&lt;input type=”tel”&gt; / type=”URL”&gt; / type=”numeric”&gt;                | Input amb validació                                                |
| &lt;input type="range" name="price" id="price" min="50000" max="500000" step="100" value="250000"&gt;  | Crea un slider (control per filtrar preu màxim)                     |
| &lt;meter min="0" max="100" value="75" low="33" high="66" optimum="50"&gt;75&lt;/meter&gt; | Control meter                                         |
| &lt;input type=”submit” / “reset” / “button”&gt;                       | Envia al servidor / neteja formulari /personalitzable amb Javascipt |

Més info:

[Forms (Mozilla.org)](https://developer.mozilla.org/en-US/docs/Learn/Forms)

[Element FORM: Mètode GET vs POST](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data)

## 4.9. Altres elements: video, audio, pictures

HTML5 incorporta elements nous com &lt;video&gt;, que permet inserir un video dins
una pàgina web. Youtube i altres plataformes de video fan servir aquest element.
Alguns elements propis de HTML5:

video, audio, figure i iframe

```html
<div>
 <svg height="300" width="800">
      <defs>
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
          <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
          <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
        </linearGradient>
      </defs>
      <rect x="50" y="20" rx="20" ry="20" width="600" height="100" fill="url(#grad1)" style="fill:blue;stroke:darkblue;stroke-width:5;opacity:0.6" />
    <ellipse cx="100" cy="70" rx="85" ry="55" fill="url(#grad1)" /> 
      <text fill="#ffffff" font-size="45" font-family="Verdana" x="50" y="86">&nbsp;Pagina Web Multimedia</text>
      Sorry, your browser does not support inline SVG.
    </svg>    
</div>

<div>
<!-- HTML compatible video formats: mp4 webm ogg
     https://es.wikipedia.org/wiki/WebM -->
    <video width="320" height="240" controls
            autoplay>
    <source src ="tierra_noche_MP4_480_1_5MG.mp4">
  </video>
</div>    

<div>
    <video width="320" height="240" controls autoplay loop> 
      <source src ="./vid/escena_animacion.mp4">
      <track src="./vid/escena_animacion.srt" label="Ingles SRT" kind="subtitles" srclang="en">
      <track src="./vid/escena_animacion.vtt" label="Ingles" kind="subtitles" srclang="en" default>
      Video tag not supported. Download the video 
      <a href="./vid/escena_animacion.mp4">here</a>.
    </video>
</div>

<div>
    <audio controls autoplay>
      <source src="./vid/viper.mp3" type="audio/mp3">
      <source src="./vid/viper.ogg" type="audio/ogg">
      <p>Your browser doesn't support HTML5 audio. Here is a <a href="viper.mp3">link to the audio</a> instead.</p>
    </audio>
</div>

<figure>
    <img src="https://picsum.photos/600/400"
         width="600" height="400"
         alt="Esta es una foto aleatoria de picsum"
    >
    <figcaption>Foto aleatoria de picsum</figcaption>
</figure>

<div>
    <iframe width="800" height="600" src="https://es.wikipedia.org/wiki/Rage_Against_the_Machine" 
    title="Wikipedia Rage_Against_the_Machine" frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </iframe>
</div>

<div>
    <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d5918.938391083444!2d2.762264678464291!3d42.118837724998826!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1ses!2ses!4v1638391807509!5m2!1ses!2ses" 
    width="800" height="600" style="border:0;" allowfullscreen="" loading="lazy">
  </iframe>  
</div>
```

## 4.10. HTML5: tags semàntics i contenidor

Elements NO semàntics: &lt;div&gt; i &lt;span&gt;. Aquests contenidors no aporten informació sobre el contingut. HTML5 incorpora uns 100 tags semàntics. 
Per ex: &lt;nav&gt; per incloure una barra de navegació.

```html
  <article>
  <aside>
  <footer>
  <header>
  <section>
  <details>
  <summary>
  <main>
  <time>
```

**Activitat 10:**

Escriu en un HTML l’estructura de les dues pàgines de la imatge amb elements semàntics.

[HTML5 semantic elements](https://www.w3schools.com/html/html5_semantic_elements.asp)


## 4.11. Estils

De moment hem vist elements HTML que permeten organitzar la informació mostrada. També podem aplicar estils a cadascun dels elements individualment. Per això fem servir el llenguatge CSS. La sintaxi es:

```html
  <etiqueta style=”propietat:valor;”>
```
Per exemple, per establir el color de fons del cos de la web, fariem:

```html
<body style="background-color:powderblue;"> (nom del color o en hexadecimal)
```

Per cambiar el color del text:

```html
<h1 style="color:blue;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>
```

Per cambiar familia de la font:

```html
<h1 style="font-family:verdana;">This is a heading</h1>
<p style="font-family:courier;">This is a paragraph.</p>
```

## 4.12. CSS

CSS o Cascading Style Sheet, és un llenguatge per donar estil i presentar l’HTML. Mentre que el HTML conté el significat o contingut, CSS és la presentació del document. Els fulls d’estil no s’assemblen a HTML. El format per definir un element CSS és propietat:valor, on la propietat pot ser qualsevol característica del texte: color, tipus I tamany les fonts, posició de l’element, etc.

## 4.13. Com aplicar codi CSS a HTML?

Fins ara quan hem desenvolupat una pàgina Web, ho hem fet amb etiquetes agrupades en un sol fitxer, el qual incloïa tant el contingut web (text, imatges, taules...) com el seu format (color i mida de la lletra, imatges de fons...).

Això comporta uns problemes:
* Els llocs web tenen normalment més d’una pagina. Si volem canviar l’estil ho hem de fer a cadascuna de les pàgines.
* Les modificaciones sobre un lloc web acostumen a ser sobre el contingut, mantenint el format estàtic. Separar contingut i estil facilita el manteniment.

Tenim el següent codi CSS que canvia els encapçalaments tipus h1, posant el text de color vermell i la mida de la lletra a 20 píxels:

```css
  h1 {
    color: #ff0000;
    font-size: 20px;
  }
```

  Sintaxi:

```css
  element_html {
    propietat: valor;
    propietat: valor;
  }
```

Aquest format s’aplicarà a tots els elements h1 del web. Podem definir tantes regles com necessitem. Fins i tot, podem definir-ne diverses per a un mateix element (el resultat serà la suma de les regles).

Tenim tres formes d’aplicar CSS a HTML: inline, interna I externa:

* A l’HTML, dins de l’etiqueta (inline):

```html
<h1 style="color:#ff0000;background-color:#ffff00">
```

  Si una etiqueta ja té un estil predefinit (com és el cas de h1), el que estem fent és redefinir-lo. Només s’aplica a l’etiqueta en qüestió (no a totes!).

* A la capcelera de la pàgina web (interna). Dintre de l’element &lt;head&lt;, afegim les etiquetes &lt;style&lt; ... &lt;/style&lt;. Afecta a tots els elements del document.

```html
  <!DOCTYPE html>
  <html>
        <head>
        <title>Ejemplo de estilo a nivel global</title>
        <style>
              h1 {
                color:#ff0000;
                background-color:#ffff00;
              }
        </style>
      </head>
      <body>
        <h1>Primer t&iacute;tol</h1>
        <h1>Segundo t&iacute;tol</h1>
      </body>
  </html>
```

* En un fitxer extern. Al head, afegint l’etiqueta link amb la ubicació de l’arxiu (a href). Per defecte farem servir aquest mètode, permet tenir el codi separat i mantenir-lo més fàcilment:

```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Ejemplo de estilo a nivel global</title>
      <link rel="StyleSheet" href="estils.css" type="text/css">
    </head>
    <body>
      <h1>Primer t&iacute;tol</h1>
      <h1>Segundo t&iacute;tol</h1>
    </body>
  </html>
```

Pot ser que apliquem estils de les 3 formes diferents en el mateix document. En aquest cas, s’aplicarà seguint el següent ordre de prioritat (1 més prioritari, 3 menys):

1. Element
2. A la pàgina
3. Fitxer extern

## 4.14. Selectors, propietats, valors.

Mentre que a HTML tenim elements, a CSS tenim selectors. La major part d’elements HTML existeixen com a selectors, encara que CSS té selectors amb funcions avançades que no existeixen a HTML.

Exemple:

```html
body {
  font-size: 14px;
  color: navy;
}
```

Pel selector body (tota la pàgina), existeixen les propietats font-size i color dintre del símbols { } que canviaran el color de fons a navy I el tamany de la font a 14px, Apart de la unitat pixels (px), podem utilitzar altres: cm, mm, %, em, rem. Alguns colors estan predefinits però també es poden especificar de moltes formes:

red
rgb(255,0,0)
rgb(100%,0%,0%)
#ff0000 (Hexadecimal)

Les propietats estan definides prèviament I no totes les propietats es poden aplicar a tots els elements. Aquí podeu trobar un llistat de totes les propietats:
https://www.w3schools.com/cssref/

Apart dels selectors d’HTML, a CSS també podem crear els nostres propis selectors. Si tenim els següent codi HTML:

```html
  <body>
    <p>Lorem ipsum dolor sit amet...</p>
    <p>Nunc sed lacus et est adipiscing accumsan...</p>
    <p>Class aptent taciti sociosqu ad litora...</p>
  </body>
```

Com podem aplicar un estil únicament a un des paràgrafs (per exemple, al primer)? Utilitzant els selectors de classe o els selectors d’ID

## 4.15. Selecció per classe

El selector per classe és un nom precedit per un punt (“.”). Afectarà a tots els elements de la mateixa classe:

CSS:

```css
  .p_vermell {
    color: red;
  }
```

HTML:

```html
<body>
  <p class="p_vermell">Lorem ipsum dolor sit amet...</p>
  <p>Nunc sed lacus et <a href="#" class="p_vermell">est adipiscing</a>
  accumsan...</p>
  <p>Class aptent taciti <em class="p_vermell">sociosqu ad</em>
  litora...</p>
</body>
```

Formes avançades de selecció:

Potser volem únicament que s’apliqui als &lt;p&gt; que tinguin definida la classe:

```css
  p.p_vermell {
    color: red;
  }
```

O aquells que siguin de la classe, i que siguin fills de &lt;p&gt;:

```css
  p .p_vermell {
    color: red;
  }
```

O a tots els elements &lt;p&gt; i els elements que siguin de la classe:

```css
  p, .p_vermell {
    color: red;
  }
```

## 4.16. Selecció per ID

El selector per classe és un nom precedit per un caràcter coixinet (“#”). Afectarà només a l’element que contingui aquell ID. NO ES POT REPETIR UN ID AL MATEIX DOCUMENT.
El funcionament és similar al concepte classe:

```html
  <body>
    <p>Lorem ipsum dolor sit amet...</p>
    <p id=”destacat”>Nunc sed lacus et est adipiscing accumsan...</p>
    <p>Class aptent taciti sociosqu ad litora...</p>
  </body>
```

CSS:
```css
  #destacat {
    color: red;
  }
```

## 4.17. Selectors pseudoclasses

Els pseudoselectors serveixen per a aplicar un estil a un element HTML que es trobi en un estat concret. És molt útil amb els elements del tipus hipervincle: <a>

Sintaxi:
```css
selector:pseudo_classe {
  propietat: valor;
}
```

Estats de <a>:

* Sense visitar - link
* Visitat - visited
* El ratolí sobre l’enllaç, però sense fer click - hover
* Amb el focus sobre l’enllaç - active

Han d’estar definides seguint aquest ordre (no cal definir-les totes, però si en ordre).

Exemple:
```css
a:visited {
  color: red;
}
```

[HTMLDog Gudes](https://htmldog.com/guides/)
