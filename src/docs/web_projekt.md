# Štruktúra zdrojových súborov

```
.
├── java
│   └── sk.fri.uniza
│   ├── api	#Reprezentácia komunikáčných objektov REST rozhrania.
│   │   ├── AccessToken.java
│   │   ├── LoginApi.java
│   │   ├── OauthRequestBuilder.java
│   │   ├── OauthRequest.java
│   │   ├── Paged.java #Kontajner pre stránkované dáta
│   │   ├── PersonBuilder.java
│   │   ├── Person.java
│   │   ├── Phone.java
│   │   ├── PublicKey.java
│   │   └── Saying.java
│   ├── auth	#Autentifikácia a autorizácia
│   │   ├── CustomAuthenticator.java
│   │   ├── CustomAuthFilter.java
│   │   ├── CustomSecurityContext.java
│   │   ├── OAuth2Authenticator.java
│   │   ├── OAuth2Authorizer.java
│   │   ├── Role.java
│   │   ├── Session.java	#Objekt relácie, ktorá je reprezentuje jedno spojenie klienta s web serverom. Tento objekt je serializovaní a uložený v Cookies prehliadača.
│   │   └── Sessions.java	#In-memory databaza všetkých relácii, ktoré server nadviazal. 
Po reštarte web servera sú všetky relázie zabudnuté, čo spôsobí odhlásenie všetkých prihlásených užívateľov.
V realnom prostredí treba tieto relácie ukladať.
│   ├── cli
│   ├── client
│   │   └── WindFarmRequest.java #Retrofit klient, ktorý sa pripája na Windfarm servis
│   ├── configuration	#POJO objekty mapujúce config.yml
│   │   ├── ServiceConnector.java 
│   │   ├── ServiceDbAuth.java
│   │   └── WindFarmDemoConfiguration.java
│   ├── core	#Triedy, ktoré nie sú používané v API, obyčajné POJO objekty
│   │   ├── UserBuilder.java
│   │   └── User.java
│   ├── db
│   │   └── BasicDao.java
│   ├── health
│   │   └── TemplateHealthCheck.java
│   ├── resources
│   │   ├── HelloWorldResource.java
│   │   ├── LoginResource.java
│   │   └── PersonsResource.java
│   ├── views	#Triedy, ktoré vytvárajú webové stránky 
│   │   ├── ErrorView.java	#Zobrazenie chybovaj hlášky
│   │   ├── GraphView.java	#Zobrazenie grafou
│   │   ├── LoginView.java	#Zobrazenie úvodnej stránky s možnostou prihlásenia do systému
│   │   ├── MaterializeFooter.java	#Päta stránky
│   │   ├── MaterializeHeader.java	#Implemntácia hlavičky stránky. Obsahuje aj Menu
│   │   ├── MaterializePage.java	#Vytvára kostru html stránky. Abstrakná trieda, ktorú dedia ostatné stránky, kotré už vytvárajú konkrétny obsah.
│   │   ├── NewPersonView.java	#Nová osoba
│   │   ├── PagePart.java	#Rozhranie, ktoré definuje prístup k šablone, ktorá tvorí stránku
│   │   ├── PersonsView.java	#Zoznam užívateľov
│   │   ├── PersonView.java	#Info o užívateľovi
│   │   └── ValidationErrorView.java	#Zobrazenie porušení validačných anotácií.
│   └── WindFarmDemoApplication.java	#Hlavná aplikácia
└── resources
    ├── assets
    │   ├── css
    │   │   ├── materialize.css	#Hlavný CSS súbor používaný knižnicou 
    │   │   ├── materialize.min.css
    │   │   └── style.css	#Vlastné úpravy css mimo materialize.css
    │   ├── img
    │   │   ├── favicon.png
    │   │   ├── img_avatar.png
    │   │   ├── logo_50px.png
    │   │   ├── logo.png
    │   │   ├── logo_small.png
    │   │   ├── sample-1.jpg
    │   │   ├── windmill_small_.jpg
    │   │   ├── windmill_sunset2.png
    │   │   ├── windmill_sunset.png
    │   │   ├── windmill_sunset_small.png
    │   │   ├── windmill.xcf
    │   │   └── yuna.jpg
    │   └── js
    │       ├── Chart.min.js	#Javascript knižnica na prácu s grafmy.
    │       ├── init.js	#Ak javascript komponenty z knižnice materializecss potrebujú inicializovať, tak je to možne zapísať do tohoto súboru 
    │       ├── jquery-3.4.0.min.js	#Pomocná knižnica na efektívnejší JS.
    │       ├── materialize.js	#Javascriptové komponenty materializecss knižnice
    │       └── materialize.min.js
    ├── banner.txt
    └── sk.fri.uniza
        └── views	#Freemarker šablóny, ktoré spolu s ich java komplementárnymi triedami  vytvárajú html stránky
            ├── done_login.ftl
            ├── error_page.ftl
            ├── graphs.ftl
            ├── login.ftl
            ├── materialize_footer.ftl
            ├── materialize_header.ftl
            ├── materialize_page.ftl
            ├── menu_items.ftl	#Definované položky hlavného menu
            ├── new_person.ftl
            ├── person.ftl
            ├── persons_table.ftl
            └── validation_error_page.ftl

```

