# API Envio de Mensajes SMS

API para integración del servicio de SMS a cualquier sistema informático.

## Metodo GET Autenticación de usuario

http://go4it.supportdesk.com.mx:8083/v1/auth/usuario/password

JavaScript:
```html
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://go4it.supportdesk.com.mx__start_key__8083__end__/v1/auth/usuario/password");

xhr.send(data);
```

Respuesta:
```html
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

http://go4it.supportdesk.com.mx:8083/v1/user/token

JavaScript:
```html
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://go4it.supportdesk.com.mx__start_key__8083__end__/v1/user/token");

xhr.send(data);
```

Respuesta:
```html
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

http://go4it.supportdesk.com.mx:8083/v1/sms/apikey/apisecret

JavaScript:
```html
var data = JSON.stringify(false);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://go4it.supportdesk.com.mx__start_key__8083__end__/v1/sms/apikey/apisecret");

xhr.send(data);
```

Respuesta:
```html
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

```javascript
var SW = new BwGateway({
        // Quitar o establecer a false cuando pase a produccion
        sandbox: true,
        // Nombre de usuario de Banwire
        user: 'pruebasbw',
        // Titulo de la entana
        title: "Mi Comercio",
        // Referencia
        reference: 'testref01',
        // Concepto
        concept: 'pago de prueba',
        // Opcional: Moneda
        currency: 'MXN',
        // Opcional: Tipo de cambio definido por el comercio (En caso de seleccionar una moneda que requiera mostrar el tipo de cambio a MXN. Solo informativo). Ejemplo: 15.00
        exchangeRate: '',
        // Total de la compra
        total: "100.00",
        // Opcional: Meses sin intereses
        months: [3,6,9,12],
        // Arreglo con los items de compra
        items: [
            {
                name: "Articulo uno",
                qty: 1,
                desc: "Articulo de prueba numero uno",
                unitPrice: 10
            },
            {
                name: "Articulo dos",
                qty: 2,
                desc: "Articulo numero dos de prueba",
                unitPrice: 40
            },
            {
                name: "Otro articulo con nombre mas largo",
                qty: 2,
                desc: "Articulo numero tres de prueba con una descripcion larga",
                unitPrice: 40
            }
        ],
        cust: {
            fname: "Ricardo", //Nombre del comprador
            mname: "Gamba", //Apellido paterno del comprador
            lname: "Lavin", //Apeliido materno del comprador
            email: "prueba@banwire.com", //Email del comprador
            phone: "55555555", //Número telefónico del comprador
            addr: "Direccion 440", //Dirección del comprador (calle y número)
            city: "Mexico", //Ciudad del comprador
            state: "DF", //Estado del comprador (2 dígitos de acuerdo al formato ISO)
            country: "MEX", //País del comprador (3 dígitos de acuerdo al formato ISO)
            zip: "14145" //Código de postal del comprador
        },
        ship: {
            addr: "Direccion 440", //Dirección de envío
            city: "Mexico", //Ciudad de envío
            state: "DF", //Estado de envío (2 dígitos de acuerdo al formato ISO)
            country: "MEX", //País de envío (3 dígitos de acuerdo al formato ISO)
            zip: "14145" //Código de postal del envío
        },
        // Opciones de pago, por defecto es "all". Puede incluir varias opciones separadas por comas
        paymentOptions: 'all', // visa,mastercard,amex,oxxo,speifast,all
        // Mostrar o no pagina de resumen de compra
        reviewOrder: true,
        // Mostrar o no mostrar los campos de envio
        showShipping: true,
        // Solamente para pagos recurrentes o suscripciones
        recurring: {
            // Cada cuanto se ejecutará el pago "month","year" o un entero representando numero de días
            interval: "month",
            // Opcional: Limitar el número de pagos (si no se pone entonces no tendrá limite)
            limit: 10, 
            // Opcional: Fecha del primer cargo (en caso de no especificar se ejecutará de inmediato)
            start: "2014-01-01", // Formaro YYYY-MM-DD
            // Opcional: En caso de que los pagos subsecuentes (después del primero)
            // tengan un monto distinto al inicial
            total: "50.00"
        },
        // URL donde se van a enviar todas las notificaciones por HTTP POST de manera asoncrónica
        notifyUrl: "https://www.mipagina.com/recibir.php",
        // Handler en caso de exito en el pago
        successPage: 'http://google.com',
        onSuccess: function(data){
            alert("¡Gracias por tu pago!")
        },
        // Pago pendiente OXXO
        pendingPage: 'http://yahoo.com',
        onPending: function(data){
            alert("El pago está pendiente por ser efectuado");
        },
        // Pago challenge
        challengePage: 'http://challenge.com',
        onChallenge: function(data){
            alert("Pago enviado a validaciones de seguridad");
        },
        // Handler en caso de error en el pago
        errorPage: 'http://facebook.com',
        onError: function(data){
            alert("Error en el pago");
        },
        // Cuando cierra el popup sin completar el proceso
        onCancel: function(data){
            console.log("Se cancelo el proceso");
        }
    });

function pagar() {
    // Podemos pagar con los valores por defecto
    SW.pay();
    
    /* O podemos modificar los valores antes de efectuar el pago
    SW.pay({
        total: 500,
        concept: "Concepto nuevo"
    });
    */
}
```

### Ejemplos en vivo
[Ir a la página principal del servicio](http://enviosms.com.mx)

## Hash de Seguridad
El parámetro 'hash' es un valor cifrado con el algoritmo SHA256 mediante una clave específica (API-SECRET) usando el método HMAC. Este parámetro se utilizará para poder verificar que el emisor de la notificación recibida está autorizado por el receptor, éste último deberá validar el parámetro Hash, asegurándose que el valor cifrado coincida con el que él calcula.

Todas las Respuestas y Notificaciones que son enviadas desde BanWire en los diferentes eventos del proceso de Secure Window incluyen el parámetro 'hash'.

API-SECRET es un valor único que se genera de forma aleatoria para cada cuenta de BanWire que se encuentran utilizando el API de Secure Window. BanWire sólo revelará ésta información al usuario autorizado de la cuenta (el manejo de ésta información quedará bajo responsabilidad y propio riesgo del usuario). Si se cree o se sabe que ésta información se conoce por un  tercera o sufre algún tipo de riesgo, se debe informar inmediatamente a BanWire para que se pueda generar y proporcionar una nueva API-SECRET. Ésta información se proporcionará una vez el usuario tenga su proceso administrativo terminado, lo que incluye la firma del contrato con BanWire.
