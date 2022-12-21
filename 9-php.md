# Tema 9: PHP

## Índex de continguts

## 9.1 Resultats d'aprenentatge i continguts

### 1. Selecciona les arquitectures i tecnologies de programació web en entorn servidor, analitzant les seves capacitats i les característiques pròpies.
1. Selecció d’arquitectures i eines de programació:
+ 1.1 Models de programació en entorns client/servidor.
+ 1.2 Generació dinàmica de pàgines web.
+ 1.3 Llenguatges de programació en entorn servidor.
+ 1.4 Integració amb els servidors web.
+ 1.5 Integració amb els llenguatges de marques.
+ 1.7 Eines de programació.

### 2. Escriu sentències executables per un servidor web reconeixent i aplicant procediments d’integració del codi en llenguatges de marques.

2. Inserció de codi en pàgines web:
+ 2.1 Obtenció del llenguatge de marques per mostrar al client.
+ 2.2 Tecnologies associades: PHP, ASP, JSP, miniaplicacions de servidors (servlets), entre altres.
+ 2.3 Etiquetes per inserció de codi.
+ 2.4 Tipus de dades. Conversions entre tipus de dades. Sintaxi del llenguatge. Sentències.
+ 2.5 Variables.

### 3. Escriu blocs de sentències embeguts en llenguatges de marques, seleccionant i utilitzant les estructures de programació.

3. Programació basada en llenguatges de marques amb codi encastat:
+ 3.1 Preses de decisió.
+ 3.2 Bucles.
+ 3.3 Tipus de dades compostes.
+ 3.4 Funcions.
+ 3.5 Recuperació i utilització d’informació provinent del client web.
+ 3.6 Processament de la informació introduïda en un formulari.
+ 3.7 Comentaris.

### 4. Desenvolupa aplicacions web embegudes en llenguatges de marques analitzant i incorporant funcionalitats segons especificacions.

4. Desenvolupament d’aplicacions web utilitzant codi encastat:
+ 4.1 Manteniment de l’estat.
+ 4.2 Galetes (cookíes).
+ 4.3 Seguretat: usuaris, perfils, rols. Galetes.
+ 4.4 Autenticació d’usuaris.
+ 4.5 Adaptacions a webs existents.
+ 4.6 Proves i depuració.

## Annex 1. Instal.lació entorn de desenvolupament

Per a crear el nostre entorn de desenvolupament, necessitarem principalment dues eines.

* **Servidor web** (Apache2) que enviarà peticions a PHP per crear pàgines dinàmiques.
* El **llenguatge de programació PHP** incrustat en pàgines HTML.

Per a instal.lar aquest programari, ho podem fer individualment en cadascuna de les nostres màquines, però és molt probable que cadascun tingui un sistema operatiu diferent, altre software que afecti al funcionament del servidor, etc. per tant cal crear un entorn de programació homogeni. A sobre Apache es fa servir típicament a Linux. 

Per tal de crear aquest entorn, utilitzarem la tècnica de virtualització amb Virtualbox, que ens permet tenir un S.O. virtual sobre el nostre hardware. Per automatitzar la instal.lació les màquines virtuals utilitzarem Vagrant. **Vagrant** permet automatitzar la instal.lació i configuracio de màquines vituals.

Per tant, els passos aseguir per a tenir el nostre entorn de desenvolupament serien:

* Descarregar [VirtualBox](https://www.virtualbox.org/wiki/Downloads "VirtualBox Downloads") e instal.lar-ho. 
* Descarregar [Vagrant](https://developer.hashicorp.com/vagrant/downloads) e instal.lar-ho.

