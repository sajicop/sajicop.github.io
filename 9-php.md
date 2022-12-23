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

Per a instal.lar aquest programari, ho podem fer individualment en cadascuna de les nostres màquines, però és molt probable que cadascun tingui un sistema operatiu diferent, software o configuracions que afectin al funcionament del servidor. Per tal de crear un entorn de programació homogeni, tenint en compte que Apache es fa servir típicament a Linux, utilitzarem màquines virtuals.

Per tal de crear aquest entorn, utilitzarem la tècnica de virtualització amb Virtualbox, que ens permet instal.lar un S.O. virtual sobre el nostre hardware. Per automatitzar la instal.lació les màquines virtuals (MV) utilitzarem Vagrant. **Vagrant** permet automatitzar la instal.lació i configuracio de màquines vituals.

Per tant, els passos aseguir per a tenir el nostre entorn de desenvolupament serien:

* Descarregar [VirtualBox](https://www.virtualbox.org/wiki/Downloads "VirtualBox Downloads") e instal.lar-ho. Si l'instal.lem a Windows, és possible que ens demani instal.lar també les llibreries de Visual C++. Hem d'instal.lar-les abans d'instal.lar Virtualbox.

* Descarregar [Vagrant](https://developer.hashicorp.com/vagrant/downloads) e instal.lar-ho.

* Vagrant és una eina de linea de comandes. Per confirmar que la tenim instal.lada, obrim la linea de comandes (**CMD** a Windows o **Terminal** a Linux) i escrivim **vagrant -v**. Ens hauria de sortir algo així:

```bash
$ vagrant -v
Vagrant 2.3.4
```
* Per començar a utilitzar la nostra MV amb Linux + Apache2 (servidor web) + PHP, farem un desplegament automàtic. Per tal de començar, crearem un directori on emmagatzemarem la nostra configuració vagrant.

```bash
$ mkdir vagrant
$ cd vagrant
```
* Una vegada dintre del directori, hem de crear dos arxius de texte i un directori:
    * **Vagrantfile**. Aquest arxiu conté la configuració de la nostra màquina virtual (nom de la màquina, RAM reservada, IP del nostre servidor, etc.).
    * **bootstrap.sh**. Aquest arxiu conté l'aprovisionament de la màquina virtual, és a dir la configuració necessària per instal.lar el servidor web i PHP. Aquest script s'executa des de l'arxiu Vagrantfile.
    * **html**. En aquest directori guardarem les nostres pàgines web amb PHP. Si no el creem la MV no arrencarà.

* El contingut de l'arxiu **Vagrantfile**:

```
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "apache2php-server"
  config.vm.synced_folder "html/", "/var/www/html"
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.provision "shell", path: "bootstrap.sh"

  config.vm.provider "virtualbox" do |v|
    v.name = "apache2php-server"
    v.memory = "1024"
    v.cpus = 1
  end
end
```
Aquí podem veure tota la informació sobre la nostra MV: v.memory (RAM), config.vm.network (tipus de xarxa i IP), etc. És pot canviar algun paràmetre si la MV no funcionés bé però recomanem mantenir-los.

* El contingut de l'arxiu **bootstrap.sh**:

```bash
#!/usr/bin/env bash

apt update
apt install apache2 -y

# Install php8 on Debian official https://packages.sury.org/php/README.txt
apt install apt-transport-https lsb-release ca-certificates curl -y
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt update && apt upgrade

# Versió actual i suportada PHP 8.1 fins finals 2024
apt install php8.1 -y

# Extensions PHP (no obligatòries)
apt install php8.1-{cli,common,xml,curl,mbstring,zip,bz2} -y
```

* Guardem els dos arxius i executem la comanda per arrencar la nostra MV:

```
vagrant up 
```

* A continuació fa un procés que processa els dos fitxers que acabem de crear. Concretament:

    * Descarrega la imatge del S.O. que li hem indicat des de els repositoris de vagrant. En el nostre cas Debian 11. Si ja la ha descarregada prèviament no la torna a descarregar i comença a muntar la MV.
    * Crea la MV amb els paràmetres que li hem indicat, habilita la xarxa a la MV per poder conectar-nos i comparteix les carpetes de la MV amb el nostre equip perquè podem treballar remotament i la nostra informació no es perdi
    * Aprovisiona la MV, és a dir instal.la el software necessari per començar a programar amb PHP. Aquesta part només la fa la primera vegada.

A partir d'aqui ja tenim l'entorn preparat i podriem obrir **Visual Studio Code** per desenvolupar els nostres scripts amb PHP. Una vegada hem acabat de programar, el procediment seria el següent.

```
vagrant halt
```
Aquesta comanda para la màquina virtual, per torna a començar, hem d'accedir al directori que hem creat (on tenim Vagrantfile) i tornar a executar ```vagrant up```.

Si en algun moment la nostra MV deixés de funcionar correctament, podem executar ```vagrant destroy```. Aquesta comanda esborra la MV i la seva definició a Virtualbox, però els nostres arxius estaran guardats al directori html. A continuació tornariem a fer ```vagrant up```.

Per conectar-nos a la MV, des de el directori on és Vagrantfile, executem ```vagrant ssh```. Allà podrem comprovar si els nostres serveis estan funcionant correctament o realitzar qualsevol modificació a la MV.

Finalment, per comprovar que tot ha anat correctament, hauriem de crear un arxiu html de prova (Hello World) i anar a la adreça http://192.168.56.10 al nostre navegador.

