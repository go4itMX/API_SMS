# API Envio de Mensajes SMS

Manual técnico para la integración del servicio de SMS a cualquier sistema informático haciendo uso de la API destinada para este fin (códigos de error al final).

## Metodo GET - Autenticación de usuario

http://api.enviosms.com.mx:8083/v1/auth/<b>usuario</b>/<b>password</b>

### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
usuario | Nombre de usuario
password | Constraseña de acceso

JavaScript:
```javascript
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://api.enviosms.com.mx__start_key__8083__end__/v1/auth/usuario/password");

xhr.send(data);
```
PHP:
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_PORT => "8083",
  CURLOPT_URL => "http://api.enviosms.com.mx:8083/v1/auth/USUARIO/PASSWORD/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

C# (Framework >=2.0):
```c#
//Este código funciona para Framework >=2.0
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/auth/USUARIO/PASSWORD");
request.Method = WebRequestMethods.Http.Get;
request.ContentType = "application/json";
request.Accept = "application/json";
var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
```

Java
```java
URL url = new URL("http://api.enviosms.com.mx:8083/v1/auth/USUARIO/PASSWORD");
HttpURLConnection conn = (HttpURLConnection) url.openConnection();
conn.setRequestMethod("GET");
conn.setRequestProperty("ContentType", "application/json");
conn.setRequestProperty("Accept", "application/json");

if (conn.getResponseCode() != 200) {
  throw new RuntimeException("Failed : HTTP error code : "
      + conn.getResponseCode());
}

BufferedReader br = new BufferedReader(new InputStreamReader(
  (conn.getInputStream())));
```

### Descripción de parámetros de salida (JSON)
Parámetro | Descripción | Tipo de dato
--- | --- | ---
status | Estatus de la respuesta | boolean
code | Código | int
token | Token | string

Ejemplo Respuesta:
Content-Type: application/json
```javascript
{
  "status": true,
  "code": 1002,
  "token": "48dueXAiOiJKV1QiLCJhbGciOiJIUzI1Nhssudy9.eyJ1c2VyIjoiZGF2aWRsIiwicGFzdyI6IiQyYS3434RFc2V2OXN1Z2duQ21HMFFQWjZCQVplUjZKSFo0R0c3NG9GSlZxOWtYTlIySGlCTUNkaGh5SyJ9.r0f8ZsdsdPzJsSEBJD_YXw7ZBtEmCLMwG98oL8AqRhqgU"
}
```
## Metodo GET - Obtener datos de usuario

http://api.enviosms.com.mx:8083/v1/user/<b>token</b>

### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
token | Token de usuario

JavaScript:
```javascript
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://api.enviosms.com.mx__start_key__8083__end__/v1/user/token");

xhr.send(data);
```
PHP:
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_PORT => "8083",
  CURLOPT_URL => "http://api.enviosms.com.mx:8083/v1/user/48dueXAiOiJKV1QiLCJhbGciOiJIUzI1Nhssudy9.eyJ1c2VyIjoiZGF2aWRsIiwicGFzdyI6IiQyYS3434RFc2V2OXN1Z2duQ21HMFFQWjZCQVplUjZKSFo0R0c3NG9GSlZxOWtYTlIySGlCTUNkaGh5SyJ9.r0f8ZsdsdPzJsSEBJD_YXw7ZBtEmCLMwG98oL8AqRhqgU",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

C# (Framework >=2.0):
```c#
//Este código funciona para Framework >=2.0
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/user/TOKEN");
request.Method = WebRequestMethods.Http.Get;
request.ContentType = "application/json";
request.Accept = "application/json";
var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
```

Java
```java
URL url = new URL("http://api.enviosms.com.mx:8083/v1/user/TOKEN");
HttpURLConnection conn = (HttpURLConnection) url.openConnection();
conn.setRequestMethod("GET");
conn.setRequestProperty("ContentType", "application/json");
conn.setRequestProperty("Accept", "application/json");

if (conn.getResponseCode() != 200) {
	throw new RuntimeException("Failed : HTTP error code : "
			+ conn.getResponseCode());
}

BufferedReader br = new BufferedReader(new InputStreamReader(
	(conn.getInputStream())));
```

### Descripción de parámetros de salida (JSON)
Parámetro | Descripción | Tipo de dato
--- | --- | ---
status | Estatus de la respuesta | boolean
code | Código | int
usuario | Nombre de usuario | string
apik | APIKEY | string
apis | APISECRET | string
balance | Crédito restante | float
price | Precio por mensaje | float
nivel | Nivel de usuario | int

Ejemplo Respuesta:
Content-Type: application/json
```javascript
{
  "status": true,
  "code": 1000,
  "usuario": "prueba",
  "apik": "O347AAA1",
  "apis": "CZYAADC3QXFVZ",
  "balance": 10,
  "price": 0.1,
  "nivel": 1
}
```

## Metodo POST - Enviar mensaje SMS

http://api.enviosms.com.mx:8083/v1/sms/<b>apikey</b>/<b>apisecret</b>

### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
apikey | API Key
apisecret | API Secret
to | Numero destino
text | Texto del mensaje (Max 509 caracteres)

### Headers
Header | Valor
--- | ---
Content-Type | Aplication/JSON

### Body (JSON)
Nombre | Valor | Tipo de dato
--- | --- | ---
to | Número a 10 dígitos | string
text | Texto SMS | string

JavaScript:
```javascript
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://api.enviosms.com.mx__start_key__8083__end__/v1/sms/apikey/apisecret");

xhr.send(data);
```
PHP:
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_PORT => "8083",
  CURLOPT_URL => "http://api.enviosms.com.mx:8083/v1/sms/APIKEY/APISECRET/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\n    to: \"5555555555\",\n    text: \"CoNTENIDO MENSAJE TEXTO\"\n}",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```
C# (Framework >=2.0) (Síncrono):
```c#
//Este código funciona para Framework >=2.0
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/sms/APIKEY/APISECRET");
var postData = "{\"to\":\"NUMERO_CELULAR\", \"text\":\"MENSAJE\"}";           
var data = Encoding.UTF8.GetBytes(postData);
request.Method = WebRequestMethods.Http.Post;
request.ContentType = "application/json";
request.ContentLength = data.Length;
request.Accept = "application/json";

using (var stream = request.GetRequestStream())
{
    stream.Write(data, 0, data.Length);
}

var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
```
C# (Framework >=4.6) (Asíncrono):
```c#
//Este código funciona para Framework >=4.6
string result = "";
string url = "http://api.enviosms.com.mx:8083/v1/sms/APIKEY/APISECRET";
string apik = "APIKEY";
string apis = "APISECRET";
string para = "NO_CELULAR" //a 10 dígitos
string mensaje = "Hello World!" //Mensaje a enviar

string envio = url + "/" + apik + "/" + apis + "/";

HttpClient client = new HttpClient();

client.BaseAddress = new Uri(envio);

// Add an Accept header for JSON format.
client.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));

HttpResponseMessage response = client.PostAsync(envio, new StringContent("{to: \"" + para + "\", text: \"" + mensaje + "\"}", Encoding.UTF8, "application/json")).Result;
var respuesta = await response.Content.ReadAsStringAsync();
```

Java
```java
URL url = new URL("http://api.enviosms.com.mx:8083/v1/sms/APIKEY/APISECRET");
String postData =  "{\"to\":\"NUMERO\", \"text\":\"MENSAJE\"}";
HttpURLConnection conn = (HttpURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestMethod("POST");
conn.setRequestProperty("ContentType", "application/json");
conn.setRequestProperty("Accept", "application/json");
OutputStream os = conn.getOutputStream();
OutputStreamWriter osw = new OutputStreamWriter(os, "UTF-8");
osw.write(postData);
osw.flush();
osw.close();

if (conn.getResponseCode() != 200) {
  throw new RuntimeException("Failed : HTTP error code : "
      + conn.getResponseCode());
}

BufferedReader br = new BufferedReader(new InputStreamReader(
  (conn.getInputStream()),"utf-8"));
```

### Descripción de parámetros de salida (JSON)
Parámetro | Descripción | Tipo de dato
--- | --- | ---
status | Estatus de la respuesta | boolean
tipo | tipo de mensaje | int
code | Código de respuesta | int
mensaje | Respuesta de la API del estatus del mensaje | string


Ejemplo Respuesta:
Content-Type: application/json
```javascript
{ 
  status: true, 
  tipo: 0, 
  codigo: 1001,
  mensaje: 'Envío en proceso'
}
```


## Metodo POST - Enviar mensaje SMS Bulk

http://api.enviosms.com.mx:8083/v1/sms/bulk/<b>apikey</b>/<b>apisecret/</b>

### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
apikey | API Key
apisecret | API Secret
to | Numeros destino separados por comas
text | Texto del mensaje (Max 509 caracteres)

### Headers
Header | Valor
--- | ---
Content-Type | Aplication/JSON

### Body (JSON)
Nombre | Valor | Tipo de dato
--- | --- | ---
to | Números a 10 dígitos separados por comas | string
text | Texto SMS | string

JavaScript:
```javascript
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://api.enviosms.com.mx__start_key__8083__end__/v1/sms/bulk/apikey/apisecret/");

xhr.send(data);
```
PHP:
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_PORT => "8083",
  CURLOPT_URL => "http://api.enviosms.com.mx:8083/v1/sms/bulk/APIKEY/APISECRET/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\n    to: \"5555555555,1234567890\",\n    text: \"CoNTENIDO MENSAJE TEXTO\"\n}",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```
C# (Framework >=2.0) (Síncrono):
```c#
//Este código funciona para Framework >=2.0
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/sms/bulk/APIKEY/APISECRET/");
var postData = "{\"to\":\"NUMERO_CELULAR1,NUMERO_CELULAR2\", \"text\":\"MENSAJE\"}";           
var data = Encoding.UTF8.GetBytes(postData);
request.Method = WebRequestMethods.Http.Post;
request.ContentType = "application/json";
request.ContentLength = data.Length;
request.Accept = "application/json";

using (var stream = request.GetRequestStream())
{
    stream.Write(data, 0, data.Length);
}

var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
```
C# (Framework >=4.6) (Asíncrono):
```c#
//Este código funciona para Framework >=4.6
string result = "";
string url = "http://api.enviosms.com.mx:8083/v1/sms/bulk";
string apik = "APIKEY";
string apis = "APISECRET";
string para = "NO_CELULAR1,NO_CELULAR2" //a 10 dígitos
string mensaje = "Hello World!" //Mensaje a enviar

string envio = url + "/" + apik + "/" + apis + "/";

HttpClient client = new HttpClient();

client.BaseAddress = new Uri(envio);

// Add an Accept header for JSON format.
client.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));

HttpResponseMessage response = client.PostAsync(envio, new StringContent("{to: \"" + para + "\", text: \"" + mensaje + "\"}", Encoding.UTF8, "application/json")).Result;
var respuesta = await response.Content.ReadAsStringAsync();
```

Java
```java
URL url = new URL("http://api.enviosms.com.mx:8083/v1/sms/bulk/APIKEY/APISECRET/");
String postData =  "{\"to\":\"NUMERO1,NUMERO2\", \"text\":\"MENSAJE\"}";
HttpURLConnection conn = (HttpURLConnection) url.openConnection();
conn.setDoOutput(true);
conn.setRequestMethod("POST");
conn.setRequestProperty("ContentType", "application/json");
conn.setRequestProperty("Accept", "application/json");
OutputStream os = conn.getOutputStream();
OutputStreamWriter osw = new OutputStreamWriter(os, "UTF-8");
osw.write(postData);
osw.flush();
osw.close();

if (conn.getResponseCode() != 200) {
  throw new RuntimeException("Failed : HTTP error code : "
      + conn.getResponseCode());
}

BufferedReader br = new BufferedReader(new InputStreamReader(
  (conn.getInputStream()),"utf-8"));
```

### Descripción de parámetros de salida (JSON)
Parámetro | Descripción | Tipo de dato
--- | --- | ---
status | Estatus de la respuesta | boolean
tipo | tipo de mensaje | int
code | Código de respuesta | int
mensaje | Respuesta de la API del estatus del mensaje | string


Ejemplo Respuesta:
Content-Type: application/json
```javascript
{ 
  status: true, 
  codigo: 1001,
  mensaje: 'Envío en proceso'
}
```
```javascript
{ 
  status: true, 
  codigo: 1003,
  mensaje: 'Envío parcialmente exitoso. 1 número(s) incorrecto(s) o con código de país inválido.'
}
```
## Códigos de error

### CÓDIGOS EXITOSOS
Código | Descripción
--- | --- 
1000 | Operación exitosa
1001 | Operación con cagargo realizada exitosamente
1002 | Autenticación exitosa
1003 | Envío parcialmente exitoso

### CÓDIGOS DE ERROR RESPUESTA HTTP
Código | Descripción| Causas
--- | --- | --- 
400 | Petición mal formada o error desconocido | Error interno inesperado
401 | No Autorizado | APIK o APIS incorrectos, Permisos insuficientes
402 | Pago Requerido | Saldo  insuficiente
404 | Recurso no encontrado | URL incorrecta

### CÓDIGOS DE ERROR JSON
Código | Descripción
--- | --- 
4000 | Error desconocido
4001 | La longitud del parametro es incorrecta
4002 | Credenciales inválidas
4004 | Permisos insuficientes
4005 | Recursos insuficientes
4007 | Nivel insuficiente
4010 | El número de teléfono no es válido

### Ejemplos en vivo
[Ir a la página principal del servicio](http://enviosms.com.mx)

## Token de Seguridad
El parámetro 'Token' es un valor cifrado con el algoritmo SHA256 mediante una clave específica (API-SECRET) usando el método HMAC. Este parámetro se utilizará para poder verificar que el emisor de la notificación recibida está autorizado por el receptor, éste último deberá validar el parámetro Hash, asegurándose que el valor cifrado coincida con el que él calcula.

API-SECRET es un valor único que se genera de forma aleatoria para cada cuenta que se encuentran utilizando el API de Secure Window. Go4IT sólo revelará ésta información al usuario autorizado de la cuenta (el manejo de ésta información quedará bajo responsabilidad y propio riesgo del usuario). Si se cree o se sabe que ésta información se conoce por un  tercera o sufre algún tipo de riesgo, se debe informar inmediatamente a Go4IT para que se pueda generar y proporcionar una nueva API-SECRET. Ésta información se proporcionará una vez el usuario tenga su proceso administrativo terminado, lo que incluye la firma del contrato con Go4IT.
