#  Tema 3. Validació de documents XML (XSD)

## 3.1. Introducció. XSD vs DTD.

Una vegada el nostre document XML és correcte sintàcticament, veurem com validar un document XML. Un document és vàlid si existeixen unes regles que defineixen quins elements aparèixen en el XML i de quin tipus (numero, texte, decimal), en quin ordre, quins són obligatoris o optatius i els atributs que conté cada element, entre altres. 

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

[CoreFiling XML Schema Validator] (http://www.corefiling.com/opensource/schemaValidate.html)


## 3.2. Estructura d'un esquema XML.

### 3.2.1. Regles XSD

Un esquema XML és un document XML que ha de complir les següents regles:

* L'element arrel s'anomena **&lt;schema&gt;**.
* L'espai de noms ha de ser [http://www.w3.org.2001/XMLSchema](http://www.w3.org.2001/XMLSchema). Es pot no usar prefixe, utilitzar xs o xsd:

```xml
      <?xml versión=”1.0”?>
      <xs:schema xmnls:xs =”http://www.w3.org.2001/XMLSchema”>
      .....
      </xs:schema>
```      

* Igual que a DTD, el primer que hem de fer és declarar l'element arrel del nostre XML. La sintaxi de **xs:element** seria:

      <xs:element name = "nombreElementoRaiz">

  Aquest element conté l'atribut name que defineix l'element arrel del document. XSD permet tenir més d'un element arrel al nostre esquema. 

```xml
      <?xml versión=”1.0”?>
        <xs:schema xmlns:xs =”http://www.w3.org.2001/XMLSchema”>
        <xs:element name=”coche” />
        <xs:element name=”barco” />
      </xs:schema>
```        

* L'ordre en que es declaren els elements (anomenats **components** a XSD) no és rellevant.

* Per a vincular un esquema amb un document XML hem d'afegir l'atribut __noNamespaceSchemaLocation__ a l'element arrel:

```xml
      <?xml version = “1.0” encoding = “UTF-8”?>
      <arrel xmlns:xsi=”http://www.w3.org/2001/XMLSchema-instance” xsi:noNamespaceSchemaLocation = “landrover.xsd”>
        ...
      </arrel>
```

A l'arxiu landrover.xsd tindrem les nostres declaracions XSD. Els blocs principals d'un esquema XSD són **xs:element** i **xs:attribute**, passem a definir-los a continuació.

## 3.2.2. Elements i tipus de dades

A XSD podem dividir els elements en ****elements simples** i **elements complexos**. Els elements simples només poden contenir texte. És a dir, no poden contenir altres fills, **ni tampoc tenir atributs**.

Atributs principals de **xs:element**:

| nom atribut | propòsit |
|-------------|----------|
| name        | nom de l'element, obligatori si és l'arrel |
| ref         | nom d'un altre element que es troba en el document |
| type        | el tipus d'element (veure tipus de dades) |
| default     | valor per defecte que pendrà l'element. Només es pot utilitzar per a continguts amb texte. |
| fixed       | indica l'únic valor possible, sempre que sigui texte. |
| minOccurs   | número mínim d'ocurrències d'un element. Els valors possibles són desde 0 fins a unbounded (il.limitat). |
| maxOccurs   | número màxim d'ocurrències d'un element. Els valors possibles són desde 0 fins a unbounded (il.limitat). |
| id          | identificador únic per a l'element |

**Tipus de dades**

Els tipus de dades més comuns a XSD són:

* xs:string (cadena)
* xs:decimal (número decimal)
* xs:integer (sencer)
* xs:boolean (veritable/fals)
* xs:date (data)
* anyURI (adreça web)

Exemples:

```xml
      <xs:element name=“dia” type=“xs:date” /> <dia>2011-09-15</dia>
      <xs:element name=“altura” type=“xs:integer”/> <altura>220</ altura >
      <xs:element name=“nombre” type=“xs:string”/> < nombre >Pere Puig</nombre >
      <xs:element name=“tamaño” type=“xs:float”/> <tamaño>1.7E2</tamaño>
```

**Activitat 8**. Explica el següent codi:

```xml
    <?xml version=”1.0”?>
      <xs:schema xmnls:xs=”http://www.w3.org.2001/XMLSchema”>
      <xs:element name=”coche” type=”xs:string” maxOccurs=”3”/>
      <xs:element name=“nombre” type="xs:string"/>
      <xs:element name=“edad” type="xs:integer" default=”18”/>
      <xs:element name=“permisoConducir” type="xs:boolean" default=”true”/>
    </xs:schema>
```    

## 3.2.3. Atributs

Fem servir el component  <xs:attribute> per especificar els atributs dels nostre document XML.

Atributs principals de **xs:attribute**:

| nom atribut | propòsit |
|-------------|----------|
|  name       | nom de l'atribut. Aquest atribut no puede aparèixer al mateix temps que ref |
|  ref        | referència a la descripció de l'atribut que es troba en altre lloc de l'esquema. Si surt aquest atribut, no apareixeran els atributs type, ni form, ni podrà contenir un component xs:simpleType |
|  type       | tipus de l'element |
|  use        | indica si l'existència de l'atribut és opcional, obligatòria o prohibida (optional, required, prohibited) |
|  default    | valor que prendrà l'atribut quan sigui procesat per alguna aplicació quan al document XML no hi té cap valor assignat. No pot aparèixer al  mateix temps que fixed |
|  fixed      | Valor únic que pot contenir el document. No pot aparèixer simultàniament amb default |
|  id         | indica identificador únic per al atribut |

Exemple:

      <xs:attribute name="alias" type="xs:string"/>
      <!-- Ahora podemos usarlo dentro de un elemento nombre -->
      <nombre alias=”Snake”> Plissken </nombre>

Un exemple complet:

  https://www.w3schools.com/xml/schema_howto.asp

**Activitat 9**.

Crea l'atribut moneda de tipus cadena que per defecte tingui el valor euro. Un atribut unitat amb tipus de dades cadena que tingui un valor fixe “minuts” i un element idEmple amb tipus de dades enter positiu i amb existència obligatòria.

## 3.3. ComplexType a XSD i exemples.

Els components es poden dividir en dos tipus: simpleType i complexType. Els tipus simpleType no poden contenir element dins, només text. Un element complexe pot contenir altres elements. Per definir-ho fem servir els elements &lt;xs:complexType&gt; i &lt;xs:sequence&gt;. L’indicador &lt;sequence&gt; implica que els elements han d’aparèixer en el mateix ordre que a la seva declaració.

Tenim el següent element XML, anomenat “empleat” que conté altres elements:

```xml
    <employee>
      <firstname>John</firstname>
      <lastname>Smith</lastname>
    </employee>
```

Per declarar l’element &lt;employee&gt; amb XSD:

```xml
    <xs:element name="employee">
      <xs:complexType>
        <xs:sequence>
          <xs:element name="firstname" type="xs:string"/>
          <xs:element name="lastname" type="xs:string"/>
        </xs:sequence>
      </xs:complexType>
    </xs:element>
```

## 3.4. Facetes

Las restriccions a XSD -també anomenades facetes- s'utilizan per a definir un rang de valors acceptable per als elements simples o atributs XML. Les restriccions a XML també s'anomenen facetes.

### 1. Restriccions per valors

El següent exemple defineix un element anomenat "age" amb una restricció. El valor de l'edat no pot ser més petita que 0 o més gran que 120.

```xml
    <xs:element name="age">
      <xs:simpleType>
        <xs:restriction base="xs:integer">
          <xs:minInclusive value="0"/>
          <xs:maxInclusive value="120"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

### 2. Restriccions per una sèrie de valors

Per limitar el contingunt d'un element XML a una sèrie acceptable de valors, farem servir la restricció d'enumeració. L'exemple que ve a continuació defineix un element anomenat "car" amb una restricció. Els únics valors acceptables son: Audi, Golf, BMW.

```xml
    <xs:element name="car">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="Audi"/>
          <xs:enumeration value="Golf"/>
          <xs:enumeration value="BMW"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

L'exemple de dalt també es pot escrire com segueix:

```xml
    <xs:element name="car" type="carType"/>
      <xs:simpleType name="carType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="Audi"/>
          <xs:enumeration value="Golf"/>
          <xs:enumeration value="BMW"/>
        </xs:restriction>
    </xs:simpleType>
```

Nota: En aquest cas el tipus "carType" es pot fer servir en altres elements perquè no és part de l'element "car".

### 3. Restriccions per una sèrie de valors (patrons)

Per limitar el contingut d'un element XML per a definir una sèrie de números o lletres que es poden fer servir, farem servir la restricció de patró.
L'exemple següent defineix un element anomenat "letter" amb una restricció, que consisteix en contenir UNA lletra MINÚSCULA (de a fins a z).

```xml
    <xs:element name="letter">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="[a-z]"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```    

En el següent exemple només s'admeten **TRES** lletres majúscules (a fins z):

```xml
    <xs:element name="initials">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="[A-Z][A-Z][A-Z]"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

En el següent exemple només s'admeten **TRES** lletres **MAJÚSCULES o MINÚSCULES**:

```xml
    <xs:element name="initials">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="[a-zA-Z][a-zA-Z][a-zA-Z]"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

En el següent exemple només s'admet **UNA** de les següents lletres x, y o z:

```xml
    <xs:element name="choice">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="[xyz]"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

Només s'accepten CINC digits en seqüència, cada dígit ha d'estar en el rang 0 fins a 9.

```xml
    <xs:element name="prodid">
      <xs:simpleType>
    <xs:restriction base="xs:integer">
    <xs:pattern value="[0-9][0-9][0-9][0-9][0-9]"/>
    </xs:restriction>
    </xs:simpleType>
    </xs:element>
```

###  4. Restriccions amb els caràcters "white-space"

Per especificar com es tracten els caracters "white-space", farem servir la restricció **whiteSpace**. 
El següent exemple defineix un element anomenat "address" amb una restricció. La restricció está establerta a "preserve", que vol dir que el processador XML no esborrarà cap caracter "white-space" (espais, tabuladors, noves línees i retorns de carro).

```xml
    <xs:element name="address">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:whiteSpace value="preserve"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

Aquest exemple utilitza **replace**, que reemplaça els caràcters **whiteSpace** amb espais:

```xml
    <xs:element name="address">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:whiteSpace value="replace"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

Aquest exemple utilitza **collapse**, que esborra tots els caràcters **whiteSpace**. Els espais en blanc múltiples es redueixen a un únic espai en blanc:

```xml
    <xs:element name="address">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:whiteSpace value="collapse"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

### 5. Restriccions de tamany

Per a limitar la longitud d'un valor en un element farem servir les restriccions **length**, **maxLength** i **minLength**.

L'exemple següent defineix un element "password" amb la restricció que el valor ha de ser exactament de vuit caràcters:

```xml
    <xs:element name="password">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:length value="8"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

Aquest exemple defineix altre element "password" amb una restricció. El valor ha de tenir mínim cinc caràcters i un màxim de vuit.

```xml
    <xs:element name="password">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:minLength value="5"/>
          <xs:maxLength value="8"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

### 6. Restriccions disponibles per als tipus de dades

| Restricció    | Descripció                                              | Valors    |
|---------------|---------------------------------------------------------|-----------|
| enumeration   | Defineix una llista de valors acceptables               |           |
| fractionDigits| Número màxim de decimals permesos                       | >= 0      |
| length        | Número exacte de caràcters o elements de llista permesos| >= 0      |
| maxExclusive  | Limit superior per valors numèrics                      | <         |
| maxInclusive  | Limit superior per valors numèrics                      | <=        |
| minExclusive  | Limit inferior per valors numèrics                      | >         |
| minInclusive  | Limit inferior per valors numèrics                      | >=        |
| maxLength     | Número máxim de caràcters o elements de llista permesos | >= 0      |
| minLength     | Número mínim de caràcters o elements de llista permesos | >= 0      |
| pattern       | Defineix la seqüència exacta de caràcters permesos      | regex     |
| totalDigits   | Especifica el número exacte de dígits                   | >= 0      |
| whiteSpace    | Especifica com es tracten els espais en blanc           | preserve replace collapse  |


### 7. Altres exemples amb restriccions

The example below defines an element called "letter" with a restriction. The acceptable value is zero or more occurrences of lowercase letters from a to z:

```xml
    <xs:element name="letter">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="([a-z])*"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

The next example also defines an element called "letter" with a restriction. The acceptable value is one or more pairs of letters, each pair consisting of a lower case
letter followed by an upper case letter. For example, "sToP" will be validated by this pattern, but not "Stop" or "STOP" or "stop":

```xml
    <xs:element name="letter">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:pattern value="([a-z][A-Z])+"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

The next example defines an element called "gender" with a restriction. The only acceptable value is male OR female:

```xml
  <xs:element name="gender">
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:pattern value="male|female"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:element>
```

The next example defines an element called "password" with a restriction. There must be exactly eight characters in a row and those characters must be lowercase or uppercase letters from a to z, or a number from 0 to 9:

```xml
  <xs:element name="password">
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:pattern value="[a-zA-Z0-9]{8}"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:element>
  ```