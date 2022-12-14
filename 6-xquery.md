# Tema 6: XQuery

## 6.1 Introducció

### **6.1.1. Base de dades**

Una base de dades (BBDD) és una eina que permet organitzar les dades que tenen algun tipus de relació entre sí, típicament emmagatzemada a un ordinador. Una base de dades és controla normalment mitjantçant un sistema gestor de base de dades (SGDB) o DBMS en anglés.

### **6.1.2. Tipus de BBDD**

Hi ha molts tipus de BBDD segons el model lògic on es descriuen les dades. 

#### **BBDD jeràrquica**

Utilitza una estructura en forma d'arbre (arrel, nodes pares/fills, nodes fulla). Són eficients per a la cerca de dades, però la seva estructura és més dificil de modificar. Permet la redundància de les dades

#### **BBDD relacional**

En aquest model no existeix jerarquia, les dades s'emmagatzemen en tuples (una fila) que formen taules (conjunt de tuples). Cada taula representa un objecte del mon real que es vol representar en un ordinador (contenen dades amb la mateixa informació semàntica). Les taules es poden relacionar entre sí amb taules intermèdies (claus primàries i claus forànees), solucionant el problema de la redundància. Fan servir el llenguatge SQL per a fer consultes.

Alguns exemples de BBDD relacionals a nivell comercial són Oracle (primer SBDG comercial) o Microsoft SQL Server. En l'àmbit Open Source tenim postgreSQL o mariaDB/mySQL.

#### **BBDD transaccional**

Poc comuns. Es fan servir a les entitats bancàries per a la transferència de diners. Permeten enviar informació a gran velocitat.

#### **BBDD noSQL**

Són bases de dades no relacionals. Algunes característiques:

* No fan servir el lleguatge SQL, les dades s'emmagatzemen en parells clau-valor. Els registres s'emmagatzemen com a documents (típicament JSON). Un exemple seria el sistema mongoDB.

### **6.1.2. SGDB**

L'ús dels SGBD és molt comú i té alguns avantatges respecte a l'ús de fitxers:

* Evita la redundància de dades.
* Evita errors de robustesa (dos programes volen modificar la mateixa dada).
* Permet la independència del Hardware i del software que gestiona la BBDD.

També té alguns inconvenients:

* No són fàcils d'administrar, es requereixen coneixements tècnics, personal especialitzat en administració de BBDD i en llenguatges de consultes.

* Si no necessitem accés concurrent a les dades (més d'un usuari vol modificar la mateixa dada), podem fer servir fitxers.

* Cost elevat en HW i SW, requereix d'un servidor.

## 6.2 Bases de dades XML


Un document XML és pot considerar una base de dades (BBDD), doncs la informació està guardada de manera estructurada, és a dir organitzada o ordenada dintre del document. Podem dir que una base de dades XML (document) permet emmagatzemar dades en format XML (format estructurat).

Les operacions que normalment es poden fer amb una BBDD com inserir, modificar o esborrar -[operacions CRUD](https://es.wikipedia.org/wiki/CRUD "Crud")- es realitzen amb els llenguatges XPath i XQuery.

Les bases de dades XML són una bona solució si la informació està estructurada de forma jeràrquica i necessitem un accés lleuger a la BBDD. Per actualitzar una columna a XML hem d'actualitzar tot el document XML. Per tant, si les dades són actualitzades molt freqüentment i els documents XML tenen moltes files (o registres) pot ser més eficients guardar les dades en una BBDD relacional. Per altra banda, si actualitzem documents petits i pocs documents al mateix temps, XML també pot ser eficient.


