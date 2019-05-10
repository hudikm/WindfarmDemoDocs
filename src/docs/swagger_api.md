# WindFarmDemo microservices

Swagger dokumentácia  je dostupna po spustení servera na adrese: `http://localhost:8085/api/swagger`

<a name="overview"></a>

## Overview

### URI scheme
*BasePath* : /api  
*Schemes* : HTTP, HTTPS


### Tags

* OAuth2 and Login
* Person resource




<a name="paths"></a>
## Resources

<a name="oauth2-and-login_resource"></a>
### OAuth2 And Login

***

<a name="showloginpage"></a>
#### Display Login page
```
GET /api/login
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Query**|**client_id**  <br>*required*|The id of the application that asks for authorization|string|
|**Query**|**redirect_uri**  <br>*required*|Holds a URL. A successful response from this endpoint results in a redirect to this URL.|string|
|**Query**|**response_type**  <br>*required*|Informs the Authorization Server of the desired authorization processing flow|enum (code, token)|
|**Query**|**scope**  <br>*required*|A space-delimited list of permissions that the application requires.|string|
|**Query**|**state**  <br>*required*|The primary reason for using the state parameter is to mitigate CSRF attacks. An opaque value, used for security purposes. If this request parameter is set in the request, then it is returned to the application as part of the redirect_uri.|string|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|[LoginPageView](#loginpageview)|


##### Produces

* `text/html`


##### Example HTTP request

###### Request path
```
/api/login?client_id=string&redirect_uri=string&response_type=string&scope=string&state=string
```


##### Example HTTP response

###### Response 200
```json
{
  "rootPath" : "string",
  "sessionId" : "string",
  "action" : "string"
}
```

***

<a name="getaccesscode"></a>
#### Request to obtain code
```
POST /api/login/code
```


##### Parameters

|Type|Name|Schema|
|---|---|---|
|**FormData**|**action**  <br>*required*|object|
|**FormData**|**password**  <br>*required*|string|
|**FormData**|**sessionId**  <br>*required*|string|
|**FormData**|**stay_signin**  <br>*required*|boolean|
|**FormData**|**username**  <br>*required*|string|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**default**|successful operation|No Content|


##### Consumes

* `application/x-www-form-urlencoded`


##### Produces

* `application/x-www-form-urlencoded`


##### Example HTTP request

###### Request path
```
/api/login/code
```


###### Request formData
```json
"string"
```

***

<a name="implicitflowauth"></a>
#### Request to obtain access token. Implicit flow
```
POST /api/login/implicit
```


##### Parameters

|Type|Name|Schema|
|---|---|---|
|**FormData**|**action**  <br>*required*|object|
|**FormData**|**password**  <br>*required*|string|
|**FormData**|**sessionId**  <br>*required*|string|
|**FormData**|**stay_signin**  <br>*required*|boolean|
|**FormData**|**username**  <br>*required*|string|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**default**|successful operation|No Content|


##### Consumes

* `application/x-www-form-urlencoded`


##### Produces

* `application/json`


##### Example HTTP request

###### Request path
```
/api/login/implicit
```


###### Request formData
```json
"string"
```

***

<a name="getpublickey"></a>
#### Request to obtain public key
```
GET /api/login/public-key
```


##### Description
An obtained public key can by used to verify JWT token


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|[PublicKey](#publickey)|


##### Produces

* `application/json`


##### Example HTTP request

###### Request path
```
/api/login/public-key
```


##### Example HTTP response

###### Response 200
```json
{
  "pubKey" : "string",
  "keyFormat" : "string",
  "keyAlg" : "string"
}
```

***

<a name="getaccesstoken"></a>
#### Request to obtain access token from code. Authorization Code
```
POST /api/login/token
```


##### Parameters

|Type|Name|Schema|
|---|---|---|
|**FormData**|**client_id**  <br>*required*|string|
|**FormData**|**client_secret**  <br>*required*|string|
|**FormData**|**code**  <br>*required*|string|
|**FormData**|**grant_type**  <br>*required*|string|
|**FormData**|**redirect_uri**  <br>*required*|string|
|**FormData**|**state**  <br>*required*|string|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**default**|successful operation|No Content|


##### Consumes

* `application/x-www-form-urlencoded`


##### Produces

* `application/json`


##### Example HTTP request

###### Request path
```
/api/login/token
```


###### Request formData
```json
"string"
```


<a name="person-resource_resource"></a>
### Person Resource

***

<a name="setpersoninfo"></a>
#### Save or update person
```
POST /api/persons
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Bearer token|string|


##### Body parameter
*Name* : body  
*Flags* : optional  
*Type* : [Person](#person)


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|[Person](#person)|


##### Produces

* `application/json`


##### Security

|Type|Name|Scopes|
|---|---|---|
|**oauth2**|**[oauth2](#oauth2)**|ADMIN,USER_READ_ONLY|


##### Example HTTP request

###### Request path
```
/api/persons
```


###### Request header
```json
"string"
```


###### Request body
```json
{
  "id" : 0,
  "userName" : "string",
  "roles" : [ "string" ],
  "email" : "string",
  "phoneNumbers" : [ {
    "owner" : {
      "id" : 0,
      "userName" : "string",
      "roles" : [ "string" ],
      "email" : "string",
      "phoneNumbers" : [ {
        "owner" : "...",
        "number" : "string",
        "id" : 0
      } ],
      "firstName" : "string",
      "lastName" : "string"
    },
    "number" : "string",
    "id" : 0
  } ],
  "firstName" : "string",
  "lastName" : "string"
}
```


##### Example HTTP response

###### Response 200
```json
{
  "id" : 0,
  "userName" : "string",
  "roles" : [ "string" ],
  "email" : "string",
  "phoneNumbers" : [ {
    "owner" : {
      "id" : 0,
      "userName" : "string",
      "roles" : [ "string" ],
      "email" : "string",
      "phoneNumbers" : [ {
        "owner" : "...",
        "number" : "string",
        "id" : 0
      } ],
      "firstName" : "string",
      "lastName" : "string"
    },
    "number" : "string",
    "id" : 0
  } ],
  "firstName" : "string",
  "lastName" : "string"
}
```

***

<a name="getlistofpersons"></a>
#### Obtain list of users
```
GET /api/persons
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Bearer token|string|
|**Query**|**limit**  <br>*optional*||integer (int32)|
|**Query**|**page**  <br>*optional*||integer (int32)|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|< [Person](#person) > array|


##### Consumes

* `application/json`


##### Produces

* `application/json`


##### Security

|Type|Name|Scopes|
|---|---|---|
|**oauth2**|**[oauth2](#oauth2)**|ADMIN|


##### Example HTTP request

###### Request path
```
/api/persons
```


###### Request header
```json
"string"
```


##### Example HTTP response

###### Response 200
```json
[ {
  "id" : 0,
  "userName" : "string",
  "roles" : [ "string" ],
  "email" : "string",
  "phoneNumbers" : [ {
    "owner" : {
      "id" : 0,
      "userName" : "string",
      "roles" : [ "string" ],
      "email" : "string",
      "phoneNumbers" : [ {
        "owner" : "...",
        "number" : "string",
        "id" : 0
      } ],
      "firstName" : "string",
      "lastName" : "string"
    },
    "number" : "string",
    "id" : 0
  } ],
  "firstName" : "string",
  "lastName" : "string"
} ]
```

***

<a name="deleteperson"></a>
#### Delete person
```
DELETE /api/persons
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Bearer token|string|
|**Query**|**id**  <br>*optional*||integer (int64)|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|[Person](#person)|


##### Security

|Type|Name|Scopes|
|---|---|---|
|**oauth2**|**[oauth2](#oauth2)**|ADMIN|


##### Example HTTP request

###### Request path
```
/api/persons
```


###### Request header
```json
"string"
```


##### Example HTTP response

###### Response 200
```json
{
  "id" : 0,
  "userName" : "string",
  "roles" : [ "string" ],
  "email" : "string",
  "phoneNumbers" : [ {
    "owner" : {
      "id" : 0,
      "userName" : "string",
      "roles" : [ "string" ],
      "email" : "string",
      "phoneNumbers" : [ {
        "owner" : "...",
        "number" : "string",
        "id" : 0
      } ],
      "firstName" : "string",
      "lastName" : "string"
    },
    "number" : "string",
    "id" : 0
  } ],
  "firstName" : "string",
  "lastName" : "string"
}
```

***

<a name="setnewpassword"></a>
#### Set new password
```
POST /api/persons/password
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Bearer token|string|
|**Query**|**id**  <br>*optional*||integer (int64)|
|**FormData**|**password**  <br>*optional*||string|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**default**|successful operation|No Content|


##### Consumes

* `application/x-www-form-urlencoded`


##### Produces

* `application/json`


##### Security

|Type|Name|Scopes|
|---|---|---|
|**oauth2**|**[oauth2](#oauth2)**|ADMIN|


##### Example HTTP request

###### Request path
```
/api/persons/password
```


###### Request header
```json
"string"
```


###### Request formData
```json
"string"
```

***

<a name="getpersoninfo"></a>
#### Find person by ID
```
GET /api/persons/{id}
```


##### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Bearer token|string|
|**Path**|**id**  <br>*required*||integer (int64)|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|successful operation|[Person](#person)|


##### Produces

* `application/json`


##### Security

|Type|Name|Scopes|
|---|---|---|
|**oauth2**|**[oauth2](#oauth2)**|ADMIN,USER_READ_ONLY|


##### Example HTTP request

###### Request path
```
/api/persons/0
```


###### Request header
```json
"string"
```


##### Example HTTP response

###### Response 200
```json
{
  "id" : 0,
  "userName" : "string",
  "roles" : [ "string" ],
  "email" : "string",
  "phoneNumbers" : [ {
    "owner" : {
      "id" : 0,
      "userName" : "string",
      "roles" : [ "string" ],
      "email" : "string",
      "phoneNumbers" : [ {
        "owner" : "...",
        "number" : "string",
        "id" : 0
      } ],
      "firstName" : "string",
      "lastName" : "string"
    },
    "number" : "string",
    "id" : 0
  } ],
  "firstName" : "string",
  "lastName" : "string"
}
```




<a name="definitions"></a>
## Definitions

<a name="loginpageview"></a>
### LoginPageView

|Name|Description|Schema|
|---|---|---|
|**action**  <br>*optional*|**Example** : `"string"`|string|
|**rootPath**  <br>*optional*|**Example** : `"string"`|string|
|**sessionId**  <br>*optional*|**Example** : `"string"`|string|


<a name="person"></a>
### Person

|Name|Description|Schema|
|---|---|---|
|**email**  <br>*optional*|**Example** : `"string"`|string|
|**firstName**  <br>*optional*|**Example** : `"string"`|string|
|**id**  <br>*optional*|**Example** : `0`|integer (int64)|
|**lastName**  <br>*optional*|**Example** : `"string"`|string|
|**phoneNumbers**  <br>*optional*|**Example** : `[ "[phone](#phone)" ]`|< [Phone](#phone) > array|
|**roles**  <br>*optional*|**Example** : `[ "string" ]`|< string > array|
|**userName**  <br>*optional*|**Example** : `"string"`|string|


<a name="phone"></a>
### Phone

|Name|Description|Schema|
|---|---|---|
|**id**  <br>*optional*|**Example** : `0`|integer (int64)|
|**number**  <br>*optional*|**Example** : `"string"`|string|
|**owner**  <br>*optional*|**Example** : `"[person](#person)"`|[Person](#person)|


<a name="publickey"></a>
### PublicKey

|Name|Description|Schema|
|---|---|---|
|**keyAlg**  <br>*optional*|**Example** : `"string"`|string|
|**keyFormat**  <br>*optional*|**Example** : `"string"`|string|
|**pubKey**  <br>*optional*|**Example** : `"string"`|string|




<a name="securityscheme"></a>
## Security

<a name="oauth2"></a>
### oauth2
oauth2

*Type* : oauth2  
*Flow* : accessCode  
*Token URL* : http://localhost:8085/api/login  
*Token URL* : http://localhost:8085/api/login/token


|Name|Description|
|---|---|
|ADMIN|Access to all resources|
|USER_READ_ONLY|Limited access|



