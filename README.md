# API Envio de Mensajes SMS

API para integración del servicio de SMS a cualquier sistema informático.

## Metodo GET Autenticación de usuario

http://api.enviosms.com.mx:8083/v1/auth/usuario/password

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

Respuesta:
Content-Typeapplication/json
```javascript
{
  "status": true,
  "code": 1002,
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiZGF2aWRsIiwicGFzdyI6IiQyYSQxMCRFc2V2OXN1Z2duQ21HMFFQWjZCQVplUjZKSFo0R0c3NG9GSlZxOWtYTlIySGlCTUNkaGh5SyJ9.r0f8ZMlPzJsSEBJD_YXw7ZBtEmCLMwG98oL8AqRhqgU"
}
```
### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
usuario | Nombre de usuario
password | Constraseña de acceso

## Metodo GET Obtener datos de usuario

http://api.enviosms.com.mx:8083/v1/token

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

Respuesta:
Content-Typeapplication/json
```javascript
{
  "status": true,
  "code": 1000,
  "usuario": "prueba",
  "apik": "O3474LA1",
  "apis": "CZYAXVDC5QXFVZ",
  "balance": 10,
  "price": 0.1,
  "nivel": 1
}
```
### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
token | Token de usuario

## Metodo POST Enviar mensaje

http://api.enviosms.com.mx:8083/v1/sms/apikey/apisecret

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

Respuesta:
Content-Typeapplication/json
```javascript
{ 
  status: true, 
  tipo: 0, 
  codigo: 1001,
  mensaje: 'Envió en proceso'
}
```
### Descripción de parámetros de entrada
Parámetro | Descripción
--- | ---
apikey | API Key
apisecret | API Secret
to | Numero destino
text | Texto del mensaje

### Ejemplos en vivo
[Ir a la página principal del servicio](http://enviosms.com.mx)

## Hash de Seguridad
El parámetro 'hash' es un valor cifrado con el algoritmo SHA256 mediante una clave específica (API-SECRET) usando el método HMAC. Este parámetro se utilizará para poder verificar que el emisor de la notificación recibida está autorizado por el receptor, éste último deberá validar el parámetro Hash, asegurándose que el valor cifrado coincida con el que él calcula.

Todas las Respuestas y Notificaciones que son enviadas desde BanWire en los diferentes eventos del proceso de Secure Window incluyen el parámetro 'hash'.

API-SECRET es un valor único que se genera de forma aleatoria para cada cuenta que se encuentran utilizando el API de Secure Window. Go4IT sólo revelará ésta información al usuario autorizado de la cuenta (el manejo de ésta información quedará bajo responsabilidad y propio riesgo del usuario). Si se cree o se sabe que ésta información se conoce por un  tercera o sufre algún tipo de riesgo, se debe informar inmediatamente a BanWire para que se pueda generar y proporcionar una nueva API-SECRET. Ésta información se proporcionará una vez el usuario tenga su proceso administrativo terminado, lo que incluye la firma del contrato con Go4IT.
