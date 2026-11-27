
**Proyecto:** Dopamine Trap · Cofre interactivo

---

## ¿Qué hace?

La tira NeoPixel es la iluminación del cofre y su forma más clara de expresar emociones. Con ella, el cofre comunica lo que está ocurriendo sin necesidad de leer la pantalla:

- **En espera:** un arcoíris suave que cambia de color lentamente e invita a jugar.
- **Durante el juego:** se ilumina del color de cada botón al mostrar la combinación y al presionarlo.
- **Al acertar:** se enciende en verde.
- **Al fallar:** parpadea en rojo junto con la alarma.

---

## Materiales

|Material|Especificación|Cantidad|
|---|---|---|
|Tira LED NeoPixel WS2812B|5 V, LEDs RGB direccionables|1 tira completa|
|Resistencia|330 Ω|1|
|Cable de calibre delgado|Rojo, verde y blanco|15 cm de cada uno|
|XIAO ESP32-C6 (XIAO JUEGO)|Controla los colores de la tira|1|

**Voltaje de operación:** 5 V. En las pruebas se alimenta desde el pin de 5 V de la XIAO, y en el armado final desde la fuente de poder.

---

## ¿Por qué elegimos esta tira?

- **Un solo pin de control:** toda la tira se maneja desde un único pin de la XIAO (D6), sin importar cuántos LEDs tenga.
- **Cada LED es independiente:** cada uno puede mostrar un color distinto, lo que permite crear efectos y animaciones.
- **Millones de colores:** cada LED combina rojo, verde y azul en distintas intensidades.
- **Fácil de programar:** con la librería Adafruit NeoPixel basta indicar qué LED y qué color se desea.
- **Flexible:** la tira puede adaptarse a la forma del cofre.

---

## ¿Cómo funciona?

Cada LED de la tira tiene un pequeño controlador integrado. La información viaja en cadena: la XIAO envía los datos al primer LED por su entrada (**DIN**); este toma su color y entrega el resto de la información al siguiente por su salida (**DO**), y así sucesivamente hasta el final de la tira.

Por eso la tira tiene una **dirección**, señalada con pequeñas flechas impresas sobre ella. Los datos solo pueden entrar por el extremo donde nacen las flechas; si se conecta por el extremo contrario, la información nunca llega a los LEDs.

Algunos detalles importantes:

- **Resistencia de 330 Ω:** se coloca en la línea de datos, entre la XIAO y la tira, para proteger el primer LED y obtener una señal más limpia.
- **Brillo moderado:** cada LED puede consumir hasta 60 mA a máxima intensidad. Para cuidar la alimentación y evitar reinicios de la XIAO, trabajamos con un brillo bajo, que además resulta suficiente y agradable a la vista.
- **Tira completa:** decidimos no cortarla y usarla como iluminación general del cofre, lo que simplificó el armado y le da un efecto más uniforme.

---

## Librerías utilizadas

Una librería es un conjunto de instrucciones ya programadas que permite controlar un componente sin escribir todo desde cero.

|Librería|¿Qué es y para qué la usamos?|
|---|---|
|**Adafruit NeoPixel**|Librería creada por Adafruit para controlar tiras y LEDs direccionables WS2812B. Se encarga de enviar la señal de datos con la velocidad y el formato exactos que necesitan los LEDs. Nos permite indicar cuántos LEDs tiene la tira, elegir el color de cada uno, ajustar el brillo y actualizar toda la tira a la vez.|

## Investigación y referencias

Para entender cómo conectar y programar este componente consultamos foros en línea y buscamos imágenes de referencia de cómo debía quedar el circuito. La mayoría de los diagramas que encontramos estaban hechos para **Arduino**, así que nos guiamos principalmente con una imagen de conexión para Arduino y la adaptamos a los pines de nuestra XIAO ESP32-C6. Esto nos obligó a entender qué función cumplía cada cable, en lugar de solo copiar la conexión.

---

## Conexiones

|Cable de la tira|Va a|
|---|---|
|Rojo (+5V)|Pin 5V de la XIAO|
|Verde (DIN)|Resistencia de 330 Ω → D6 de la XIAO JUEGO|
|Blanco (GND)|Riel de tierra (GND)|

## Una lección con final feliz

La tira llegó con su conector ya soldado de fábrica, así que dimos por hecho que ese era el lado correcto para conectarla. Revisamos el código, los cables, la resistencia y la alimentación una y otra vez, y la tira simplemente no encendía.

Después de varios intentos, al revisarla con calma, notamos que las flechas impresas apuntaban **hacia** el conector: la tira nos la habían vendido con el conector en el extremo de salida. Todo nuestro esfuerzo había sido por un detalle que no dependía de nosotros, pero que tampoco habíamos observado con atención.

Al darnos cuenta terminamos riéndonos, porque sufrimos bastante por algo tan pequeño. Fue un momento divertido que además nos dejó una enseñanza muy clara: en electrónica, los detalles importan.

### ¿Cómo lo resolvimos?

1. Identificamos el extremo de entrada, donde las flechas se alejan del borde y aparecen las marcas **+5V, DIN y GND**.
2. Soldamos tres cables nuevos en ese extremo: **+5V, DIN y GND**.
3. Utilizamos los colores **rojo, verde y blanco**, los mismos que traía la tira de origen, para mantener la continuidad y que cualquier persona del equipo pudiera identificar cada cable con facilidad.
4. El extremo con el conector de fábrica quedó sin conexión, y sus cables sueltos se aislaron por separado para evitar cortos.

Con este cambio, la tira encendió correctamente desde la primera prueba.

---

## Problemas que tuvimos y cómo los resolvimos

|Problema|Causa|Solución|
|---|---|---|
|La tira no encendía|El conector de fábrica estaba soldado en el extremo de salida|Soldamos cables nuevos en el extremo de entrada|
|Dudas sobre qué cable era cada uno|Los cables cambian de color al pasar por algunos conectores|Mantuvimos los colores originales: rojo para 5V, verde para datos y blanco para tierra|
|Riesgo de corto con los cables sueltos|El extremo de salida tenía cables de alimentación descubiertos|Aislamos cada punta por separado|

## Conclusión

La tira NeoPixel le da al cofre su ambiente y su capacidad de reaccionar con luz ante cada jugada. Su conexión es sencilla, pero nos recordó la importancia de observar cada detalle antes de dar algo por sentado. Lo que comenzó como un problema frustrante terminó siendo una de las anécdotas más divertidas del proyecto y una lección que no vamos a olvidar.

<video src="../Media/led.mov" controls width="100%"></video>
