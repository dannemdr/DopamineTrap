
**Proyecto:** Dopamine Trap · Cofre interactivo

---

## ¿Qué hace?

El buzzer es el sonido del cofre. Acompaña cada momento del juego para que el jugador sepa qué está pasando, incluso sin mirar la pantalla:

- **Una nota distinta por botón:** cada color tiene su propio sonido, lo que ayuda a memorizar las combinaciones.
- **Un tono de acierto** al completar cada nivel.
- **Una alarma** al fallar o al agotarse el tiempo.
- **Una canción de victoria** al superar el reto.

---

## Materiales

|Material|Especificación|Cantidad|
|---|---|---|
|Buzzer pasivo|2 patitas, funciona con 3.3 V|1|
|Cable de calibre delgado|Uno de color para la señal y uno negro para tierra|2|
|XIAO ESP32-C6 (XIAO JUEGO)|Genera las notas|1|

**Voltaje de operación:** trabaja directamente con la señal de 3.3 V del pin de la XIAO.

---

## Buzzer activo vs buzzer pasivo

Existen dos tipos de buzzer y, aunque por fuera se parecen, funcionan de forma muy diferente:

**Buzzer activo.** Tiene un circuito interno que siempre produce el mismo pitido. No puede tocar melodías. Se reconoce porque por debajo está completamente cerrado con resina negra.

**Buzzer pasivo.** No tiene circuito interno, así que suena con la nota que le indique la XIAO. Puede tocar canciones completas. Se reconoce porque por debajo se alcanza a ver una pequeña placa verde.

### ¿Por qué cambiamos al pasivo?

Al principio probamos con un buzzer activo, pero no funcionó para lo que buscábamos. Su sonido era muy fuerte y áspero, parecido a una alarma sísmica, y en lugar de resultar atractivo podía asustar a quien lo escuchara de repente. Para un juego pensado en niños y jóvenes, eso iba en contra de la experiencia que queríamos crear.

Gracias a nuestra compañera Ana, que nos prestó un buzzer pasivo, pudimos reproducir canciones y sonidos mucho más agradables, suaves y fáciles de escuchar.

---

## ¿Cómo funciona?

El sonido es una vibración: entre más rápido vibra algo, más aguda es la nota. Esa velocidad se mide en **hercios (Hz)**, es decir, cuántas veces vibra por segundo.

Para tocar una nota, la XIAO enciende y apaga el pin del buzzer muchas veces por segundo, exactamente a la frecuencia de esa nota. Por ejemplo, la nota Do se produce a 523 Hz y la nota Sol a 784 Hz. El entorno de Arduino incluye una instrucción llamada **tone()** que se encarga de esto: solo hay que indicarle el pin, la frecuencia y cuánto tiempo debe sonar.

Una melodía se construye con dos listas:

- **Las notas:** la frecuencia de cada sonido, en orden.
- **Las duraciones:** cuántos milisegundos dura cada nota.

El programa recorre ambas listas y deja una pausa muy breve entre nota y nota, para que cada sonido se escuche separado y la melodía sea clara.

---

## La canción de victoria

Queríamos que ganar se sintiera como un momento especial. Para inspirarnos pensamos en melodías de videojuegos que nos gustan, como las de _Zelda_ o _Angry Birds_: canciones que recuerdan buenos momentos y que hacen saber de inmediato que se logró algo.

Con esa idea con notas que suben de forma alegre y un final heroico, pensada especialmente para el buzzer. Usamos notas agudas, ya que es en ese rango donde el buzzer suena más claro y bonito.

### Sonido y luz en sintonía

Las luces del cofre acompañan a cada sonido:

|Momento|Sonido|Luz|
|---|---|---|
|Se presiona un botón|La nota de ese botón|La tira se ilumina del color del botón|
|Se completa un nivel|Tono de acierto|Verde|
|Victoria|Canción de victoria|Verde mientras suena la canción|
|Error o tiempo agotado|Alarma|Rojo parpadeante|

## Librerías utilizadas

El buzzer no necesita ninguna librería externa. La instrucción para generar notas ya viene incluida en el entorno de Arduino para la XIAO ESP32-C6.

---

## Investigación y referencias

Consultamos foros en línea y buscamos imágenes de referencia para conectar el buzzer. Como la mayoría de los ejemplos estaban hechos para **Arduino**, nos guiamos principalmente con una imagen de conexión para Arduino y la adaptamos a los pines de nuestra XIAO. También investigamos las frecuencias de las notas musicales para poder escribir la melodía.

---

## Conexiones

|Patita del buzzer|Va a|
|---|---|
|Positiva (+, la más larga)|D7 de la XIAO JUEGO|
|Negativa (−, la más corta)|Riel de tierra (GND)|

## Problemas que tuvimos y cómo los resolvimos

|Problema|Causa|Solución|
|---|---|---|
|El sonido era molesto y podía asustar|El buzzer activo solo produce un pitido fuerte y fijo|Lo cambiamos por un buzzer pasivo, gracias al préstamo de Ana|
|Algunas melodías sonaban poco claras|El buzzer suena mejor en notas agudas y con pausas entre notas|Compusimos la fanfarria en un rango agudo y separamos cada nota|
|Duda sobre cómo conectar un buzzer de 2 patitas|Los ejemplos que encontramos usaban módulos de 3 pines|Identificamos la patita positiva por ser la más larga|

## Conclusión

El buzzer demostró que un componente pequeño puede cambiar por completo la experiencia de juego. Elegir el tipo adecuado marcó la diferencia entre un sonido que asusta y uno que celebra. Junto con las luces, la canción de victoria convierte el final del reto en un momento alegre, que el jugador puede reconocer al instante.

![buzz](/Media/Buzzer.JPG)
