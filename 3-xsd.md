#  Tema 3. Validació de documents XML (XSD)

## 3.1. Introducció. XSD vs DTD.
Una vegada el nostre document XML és correcte sintàcticament, veurem com validar un document XML. Un document és vàlid si existeixen unes regles que defineixen quins elements aparèixen en el XML i de quin tipus (numero, texte, decimal), en quin ordre, quins són obligatoris o optatius, els atributs que conté cada element, etc.

Per exemple, si estem definint un document XML per als llibres una llibreria, podem decidir que per a cada llibre hem d'incloure un identificador únic (per
exemple el ISBN), el title i l'autor principal.
Podem crear un sistema per guardar tots els jugadors i equips d'una lliga de futbol. Podriem definir una regla que verifiqués que hi hagués onze elements dintre de cada equip o que un jugador no pot jugar en dos equips alhora.

Un document ben format pot ser validat amb les tecnologies DTD o XML Schema (XSD).

Document Type Definition (DTD) defineix els blocs o elements d'un document XML. DTD prové d'un subconjunt del llenguatge SGML. En la actualitat (2022)  aquest sistema no s'utilitza gaire, principalment degut a les seves limitacions.

Algunes de les seves limitacions són:

* Un document DTD no és un document XML, per tant no podem verificar que estigui ben format.
* No es poden fer restriccions sobre els diferents valors que pot pendre un element: tamany, tipus de dades, etc.
* No es pot donar un valor per defecte per als elements (si els atributs).
* No soporta espais de noms.

L'alternativa als documents DTD son els esquemes XML o XSD (XML Schema Definition). 

XSD supera totes les limitacions de DTD:

* Els documents XSD deriven de XML, per tant són documents XML i es poden comprobar sintàcticament.
* XSD defineix molts tipus de dades predefinits.
* XSD permet definir la cardinalitat dels elements.
* XSD permet mesclar diferents vocabularis XML (espais de noms).

Els XSD tenen l'inconvenient de que són lleugerament més difícils d'interpretar a diferència dels DTD.

Un Esquema XML és el motlle d'on sortiran els diferents documents XML que compliran l'estructura definida a l'esquema, cadascun amb les seves dades concretes.

Per validar els documents XML, podem fer servir les eines de programació vistes fins ara. També podem trobar alguns validadors on-line, com per exemple:

http://www.corefiling.com/opensource/schemaValidate.html


## 3.2. Estructura d'un esquema XML.

### 3.2.1. Regles XSD

Un esquema XML és un document XML que ha de complir les següents regles:

* L'element arrel s'anomena &lt;schema&gt;.
* L'espai de noms ha de ser http://www.w3.org.2001/XMLSchema. Es pot no usar prefixe, o utilitzar xs o xsd:

      <?xml versión=”1.0”?>
      <xs:schema xmnls:xs =”http://www.w3.org.2001/XMLSchema”>
      .....
      </xs:schema>

* Igual que a DTD, hem de declarar l'element arrel del nostre XML, la seva sintaxis seria:

      <xs:element name = "nombreElementoRaiz">

Aquest element conté l'atribut name que defineix l'element arrel del document. Podem tenir més d'un element arrel al nostre esquema.

      <?xml versión=”1.0”?>
        <xs:schema xmlns:xs =”http://www.w3.org.2001/XMLSchema”>
        <xs:element name=”coche” />
        <xs:element name=”barco” />
      </xs:schema>

* L'ordre en que es declaren els elements (anomenats components a XSD) no és rellevant.* 
* Per a vincular un esquema amb un document XML, al nostre XML afegirem dos atributs a l'element arrel:

    <?xml version = “1.0” encoding = “UTF-8”?>
    <coches xmlns:xsi=”http://www.w3.org/2001/XMLSchema-instance” xsi:noNamespaceSchemaLocation = “landrover.xsd”>
      ...
    </coches>


A l'arxiu landrover.xsd tindriem les nostres declaracions XSD. Els components principals d'un esquema són xs:schema i xs:element. El components de tipus xs:element poden ser de tipus simpleType o complexType. Els elements simpleType només poden tenir un valor de text, no poden contenir altres elements o atributs.

Atributs principals de xs:element:
* name: indica el nom de l'element, obligatori si és l'arrel.
* ref: indica el nom d'un altre element que es troba en el document.
* type: indica el tipus d'element (veure a continuació).
* default: valor per defecte que pendrà l'element. Només es pot utilitzar per a continguts amb texte.
* fixed: indica l'únic valor possible, sempre que sigui texte.
* minOccurs: número mínim d'ocurrències d'un element dintre del document XML. Els valors possibles són desde 0 fins a unbounded (il.limitat).
* maxOccurs: número màxim d'ocurrències d'un element dintre del document XML. Els valors possibles són desde 0 fins a unbounded (il.limitat).
* id: identificador únic per a l'element

## 3.2.2. Tipus de dades

Els tipus de dades més comuns a XSD són:

* xs:string (cadena)
* xs:decimal (número decimal)
* xs:integer (sencer)
* xs:boolean (veritable/fals)
* xs:date (data)
* anyURI (adreça web)

      <xs:element name=“dia” type=“xs:date” /> <dia>2011-09-15</dia>
      <xs:element name=“altura” type=“xs:integer”/> <altura>220</ altura >
      <xs:element name=“nombre” type=“xs:string”/> < nombre >Pere Puig</nombre >
      <xs:element name=“tamaño” type=“xs:float”/> <tamaño>1.7E2</tamaño>

Activitat 8. Explica el següent codi:

    <?xml version=”1.0”?>
      <xs:schema xmnls:xs=”http://www.w3.org.2001/XMLSchema”>
      <xs:element name=”coche” type=”xs:string” maxOccurs=”3”/>
      <xs:element name=“nombre” type="xs:string"/>
      <xs:element name=“edad” type="xs:integer" default=”18”/>
      <xs:element name=“permisoConducir” type="xs:boolean" default=”true”/>
    </xs:schema>

## 3.2.3. Atributs

Els atributs principals son:
* name: nom de l'atribut. Aquest atribut no puede aparèixer al mateix temps que ref.
* ref: referència a la descripció de l'atribut que es troba en altre lloc de l'esquema. Si surt aquest atribut, no apareixeran els atributs type, ni form, ni podrà contenir un component &lt;xs : simpleType&gt;
* type: tipus de l'element.
* use: indica si l'existència de l'atribut és opcional, obligatòria o prohibida (optional, required, prohibited).
* default: valor que prendrà l'atribut quan sigui procesat per alguna aplicació quan al document XML no hi té cap valor assignat. No pot aparèixer al  mateix temps que fixed.
* fixed: Valor únic que pot contenir el document. No pot aparèixer simultàniament amb default.
* id: indica identificador únic per al atribut.

Exemple:

      <xs:attribute name="alias" type="xs:string"/>
      <!-- Ahora podemos usarlo dentro de un elemento nombre -->
      <nombre alias=”Snake”> Plissken </nombre>

Un exemple complet:
https://www.w3schools.com/xml/schema_howto.asp

**Activitat 9**.
Crea l'atribut moneda de tipus cadena que per defecte tingui el valor euro. Un atribut unitat amb tipus de dades cadena que tingui un valor fixe “minuts” i un element idEmple amb tipus de dades enter positiu i amb existència obligatòria.

## 3.3. Components XSD i exemples.

Els components es poden dividir en dos tipus: simpleType i complexType. Els tipus simpleType no poden contenir element dins, només text. Un element complexe pot contenir altres elements. Per definir-ho fem servir els elements &lt;xs:complexType&gt; i &lt;xs:sequence&gt;. L’indicador &lt;sequence&gt; implica que els elements han d’aparèixer en el mateix ordre que a la seva declaració.

Tenim el següent element XML, anomenat “empleat” que conté altres elements:

    <employee>
      <firstname>John</firstname>
      <lastname>Smith</lastname>
    </employee>

Per declarar l’element &lt;employee&gt; amb XSD:

    <xs:element name="employee">
      <xs:complexType>
        <xs:sequence>
          <xs:element name="firstname" type="xs:string"/>
          <xs:element name="lastname" type="xs:string"/>
        </xs:sequence>
      </xs:complexType>
    </xs:element>


