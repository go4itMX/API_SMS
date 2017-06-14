# API Envio de Mensajes SMS

Manual técnico para la integración del servicio de SMS a cualquier sistema informático haciendo uso de la API destinada para este fin.

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

C#:
```c#
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/auth/USUARIO/PASSWORD");
request.Method = WebRequestMethods.Http.Get;
request.ContentType = "application/json";
request.Accept = "application/json";
var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
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

C#:
```c#
var request = (HttpWebRequest)WebRequest.Create("http://api.enviosms.com.mx:8083/v1/user/TOKEN");
request.Method = WebRequestMethods.Http.Get;
request.ContentType = "application/json";
request.Accept = "application/json";
var response = (HttpWebResponse)request.GetResponse();
var responseString = new System.IO.StreamReader(response.GetResponseStream()).ReadToEnd();
```

### Descripción de parámetros de salida (JSON)
Parámetro | Descripción | Tipo de dato
--- | --- | ---
status | Estatus de la respuesta | boolean
code | Código | int
usuario | Nombre de usuario | string
apik | APIKEY | string
apis | APISECRET | string
balance | Crédito restante | int
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
C#:
OPCION SÍNCRONA:
```c#
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
OPCION ASÍNCRONA:
```c#
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

HttpResponseMessage response = client.PostAsync(envio, new StringContent("{to: \"" + para + "\", text: \"" + mensaje + "\"}", Encoding.UTF8)).Result;
var respuesta = await response.Content.ReadAsStringAsync();
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
  mensaje: 'Envió en proceso'
}
```

### Ejemplos en vivo
[Ir a la página principal del servicio](http://enviosms.com.mx)

## Token de Seguridad
El parámetro 'Token' es un valor cifrado con el algoritmo SHA256 mediante una clave específica (API-SECRET) usando el método HMAC. Este parámetro se utilizará para poder verificar que el emisor de la notificación recibida está autorizado por el receptor, éste último deberá validar el parámetro Hash, asegurándose que el valor cifrado coincida con el que él calcula.

API-SECRET es un valor único que se genera de forma aleatoria para cada cuenta que se encuentran utilizando el API de Secure Window. Go4IT sólo revelará ésta información al usuario autorizado de la cuenta (el manejo de ésta información quedará bajo responsabilidad y propio riesgo del usuario). Si se cree o se sabe que ésta información se conoce por un  tercera o sufre algún tipo de riesgo, se debe informar inmediatamente a Go4IT para que se pueda generar y proporcionar una nueva API-SECRET. Ésta información se proporcionará una vez el usuario tenga su proceso administrativo terminado, lo que incluye la firma del contrato con Go4IT.
