# Úvod

Windfarmdemo je aplikácia postavená na frameworku [dropwizard](https://www.dropwizard.io/), ktorý je poskladaný z nasledujúcich knižníc:

- [Jetty](http://www.eclipse.org/jetty/) HTTP web server.
- [Jersey](https://jersey.github.io/)  RESTové rozhranie.
- [Jackson](https://github.com/FasterXML/jackson) JSON serializovanie a deserializovanie.
- [Logback](http://logback.qos.ch/) logovanie.
- [Hibernate Validator](http://hibernate.org/validator/) validovanie dát'.
- [Metrics](http://metrics.dropwizard.io/) na to, aby sme zistili „čo robí vaša aplikácia“ 
- [JDBI](http://www.jdbi.org/) a [Hibernate](http://www.hibernate.org/orm/) databáza
- [Liquibase](http://www.liquibase.org/) migrácia.
- [FreeMarker](https://freemarker.apache.org/) a [mustache](https://mustache.github.io/) generovanie webových stránok



### Ukážková aplikácia

Táto aplukácia demoštruje použitie nasladujúcich knižníc a častí dropwizardu:

- REST rozhranie vytvorené za pomoci Jersey resp. JAX-RS API. Implementované v priečinku `Resources`
- Využitie databázy za pomoci Hibernate frameworku
  - `PersonDao` ilustruje použitie DAO(data access objekt) objektu pristupujúceho k dátam s použitím hibernate. Na prístup k dátam sa používa ako jazyk `HQL` tak aj prístup pomocou `JPA Criteria API` 
  - `Person` ilustruje mapovanie Java objektov na tabuľky v databáze použitím JPA anotácií. 
  - Aplikácia obsahuje implementáciu autorizačného OAuth2 servisu, ktorý implementuje dva základné toky `implicit, code`. Tento servis sa dá použiť na generovanie JWT prístupových tokenov.
  - Jednotlivé REST zdroje sú zabezpečené pomocou OAuth2  prístupového tókenu. 



## Požiadavky na spojenie s DB

Aplikácia na spustenie vyžaduje existujúcu databázu MariaDB s nasledujúcimi parametrami:

- URL: `localhost:3306`
- Typ databázy: `MariaDB`
- Názov vyvorenej databázy: `windfarmdemoDB`
- Užívatel: `windfarmdemo`
- Heslo: `G1PpyytVE8Zy8kHE`

Štandardné nastavenie môžete zmeniť v súbore: `config.yml`

!!!note "Inštalácia MariaDB"
     Na inštalovanie databázy odporúčam použiť balík XAMPP, ktorý obsahuje Apache + MariaDB + PHP + Perl. Databázu može konfigurovať pomocou PHPmyadmin prostredia.   [XAMPP](https://www.apachefriends.org/index.html)

## Odkazy

REST klient a JSON

- [**Retrofit**](http://square.github.io/retrofit/) : Typovo bezpečný HTTP klient pre Android a Java 
- [**jsonschema2pojo**](http://www.jsonschema2pojo.org/) **:** Generátor POJO objektov pre Java jazyku s JSON alebo JSON-Schema
- [**reqres.in**](https://reqres.in/) : Testovacie REST API
- <https://jsonplaceholder.typicode.com/>

Dropwizzard:

- [Docs](http://www.dropwizard.io/1.3.9/docs/getting-started.html)
- [Jax-RX api](https://jersey.github.io/documentation/latest/jaxrs-resources.html)

OAuth2.0:

- [OAUTH/OPENID](https://hackernoon.com/demystifying-oauth-2-0-and-openid-connect-and-saml-12aa4cf9fdba
  https://youtu.be/996OiexHze0
  http://dmpc.dbp.fmph.uniba.sk/~rybar/it-software/docs/infoware-OpenID.pdf
  https://developer.okta.com/blog/2018/05/24/what-is-the-oauth2-implicit-grant-type
  )
- [Prednáška](https://youtu.be/996OiexHze0)
- [Implicit flow](https://developer.okta.com/blog/2018/05/24/what-is-the-oauth2-implicit-grant-type)
- [Code flow](https://developer.okta.com/blog/2018/04/10/oauth-authorization-code-grant-type)

Bezpečnosť

- [Custum Authenticaion](https://spin.atomicobject.com/2016/07/26/dropwizard-dive-part-1/)
- [HTTPS](https://dzone.com/articles/getting-started-dropwizard-0)

Hibernate:

- [Hibernate rôzne návody](https://www.baeldung.com/tag/hibernate/)
- [Metamodel generator](https://docs.jboss.org/hibernate/orm/5.3/topical/html_single/metamodelgen/MetamodelGenerator.html)
- [Getting started](http://docs.jboss.org/hibernate/orm/5.4/quickstart/html_single/)
- [Dokumentácia](http://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html)

Freemarker:

- [Dokumentácia](https://freemarker.apache.org/docs/index.html)

Css šablóna:

- [Materializecss](https://materializecss.com)

Javascript:
- [Jquery  knižnica](http://jquery.com/)
- [Grafy](https://www.chartjs.org/docs/latest/)

Swagger - generátor api dokumentácie:

- [Java anotácie](https://github.com/swagger-api/swagger-core/wiki/Swagger-2.X---Annotations) 

- [Swagger](https://swagger.io/)

