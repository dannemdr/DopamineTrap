### Inicio Simple, final podrido

Al principio yo ya tenia certeza de lo que mostraba y como hacer el código de la presentación porque mi equipo ya lo había echo, en si nadamas tomando en cuenta el código principal, cambiándole la contraseña y el nombre ya debería de ser una diferente y con otras letras. 

![Codigo](Media/Pipo_Codigo.png)

### Captura de pantalla y código arreglado 

Después de ya saber que hacer pero por mi mismo no hacer las pruebas, primero intentamos usar la misma Xiao para dos laptops, al conectarla, cambiarle el nombre, la contraseña y lo que dice la Xiao, pues debería ya poder cambiar y hacer lo mismo que hizo en la anterior laptop. Pero al momento de ya activarlo, salía el nombre de la anterior red, y no la actualización, entonces al verificar que todo estaba bien, resetear la Xiao, encontré que lo que estaba mal y el porque no daba el nuevo nombre y las nuevas palabras o instrucciones era porque no se le había cambiado la contraseña correctamente, al no ponerle una contraseña de 8 caracteres, seguía sin actualizar la Xiao con esas nuevas instrucciones y por eso si prendía y mostraba red pero de la anterior instrucción.  


![Prueba final Celular](Media/CapRed.jpeg)



### Código ahora si con la contraseña de 8 caracteres o mas 

``` 
#include <WiFi.h>

#include <WebServer.h>

  

WebServer server(80);

  

const int SENSOR = A0;   // tu pin

const int SALIDA = D2;

  

void handleRoot() {

  int v = analogRead(SENSOR);

  String html = "<html><head>"

                "<meta name='viewport' content='width=device-width'>"

                "<meta http-equiv='refresh' content='2'>"

                "</head><body><h1>Mi proyecto</h1>"

                "<p>Sensor: " + String(v) + "</p>"

                "<p>Porfin profe :) </p>"

                "<a href='/on'>Encender</a> <a href='/off'>Apagar</a>"

                "</body></html>";

  server.send(200, "text/html", html);

}

  

void setup() {

  Serial.begin(115200);

  pinMode(SALIDA, OUTPUT);

  digitalWrite(SALIDA, LOW);

  

  WiFi.softAP("KIRK", "6767676767");

  Serial.println(WiFi.softAPIP());

  

  server.on("/", handleRoot);

  

  server.on("/on", []() {

    digitalWrite(SALIDA, HIGH);

    server.sendHeader("Location", "/");

    server.send(303);

  });

  

  server.on("/off", []() {

    digitalWrite(SALIDA, LOW);

    server.sendHeader("Location", "/");

    server.send(303);

  });

  

  server.begin();

}

  

void loop() {

  server.handleClient();

}
```

## Conclusiones 
Hacer todo desde cero sin tener saltos de procesos y verificar que todo, absolutamente todo lo escrito en código sea correcto o tenga coherencia, perdón profe :(.