
**Proyecto:** Dopamine Trap · Cofre interactivo

---

## ¿Qué hace?

La pantalla OLED es la voz del cofre. Ubicada en la boca, entre los dientes, es la encargada de comunicarse con el jugador: le da la bienvenida, le muestra la combinación que debe memorizar, le indica cuándo es su turno y le avisa si ganó o si debe esperar un castigo.

---

## Materiales

|Material|Especificación|Cantidad|
|---|---|---|
|Pantalla OLED SSD1306|0.96", 128 × 64 píxeles, comunicación I2C, 4 pines|1|
|XIAO ESP32-C6 (XIAO JUEGO)|Microcontrolador que envía la información a la pantalla|1|
|Jumpers|Conexión entre la pantalla y la protoboard|4|

**Voltaje de operación:** la pantalla funciona entre 3.3 V y 5 V. En nuestro caso se alimenta con **3.3 V** directamente desde la XIAO.

---

## ¿Por qué elegimos esta pantalla?

- **Solo necesita 4 cables:** dos de alimentación (VCC y GND) y dos de comunicación (SDA y SCL), lo que mantiene el cableado limpio dentro del cofre.
- **Comunicación I2C:** varios dispositivos pueden compartir los mismos dos cables, lo que nos deja pines libres para los botones, la tira de luces y el buzzer.
- **Compatible con 3.3 V:** se conecta directamente a la XIAO, sin componentes adicionales.
- **Alto contraste:** cada píxel emite su propia luz, por lo que el texto se lee con claridad incluso a poca luz y desde distintos ángulos.
- **Bajo consumo:** solo gastan energía los píxeles encendidos.
- **Fácil de programar:** las librerías Adafruit SSD1306 y Adafruit GFX permiten escribir texto, cambiar su tamaño y moverlo con pocas instrucciones.
- **Tamaño compacto:** cabe con naturalidad en la boca del cofre, como parte de su personaje.

---

## ¿Cómo funciona?

La pantalla se comunica con la XIAO mediante el protocolo **I2C**, que utiliza dos líneas:

- **SDA (datos):** por donde viaja la información de lo que se va a dibujar.
- **SCL (reloj):** marca el ritmo de la comunicación para que ambos dispositivos estén sincronizados.

Cada dispositivo I2C tiene una dirección propia; la de nuestra pantalla es **0x3C**. El programa primero prepara la imagen completa en la memoria de la XIAO y después la envía a la pantalla de una sola vez. Esto evita parpadeos y hace que los cambios se vean fluidos.

---

## Conexiones

|Pin de la OLED|Va a|
|---|---|
|GND|Riel de tierra (GND)|
|VCC|Riel de 3.3 V|
|SCL|D5 de la XIAO JUEGO|
|SDA|D4 de la XIAO JUEGO|

## El letrero en movimiento

Al montar la pantalla nos dimos cuenta de que era más pequeña de lo que esperábamos. Con letra normal, los mensajes se veían diminutos, y si aumentábamos el tamaño ya no cabían completos.

Gracias a la creatividad de nuestro profesor y asesor Rafael, encontramos una solución: hacer que el texto se desplace como los letreros luminosos de los puestos de comida o de las grandes ciudades. Así podemos usar letras grandes y legibles, y el mensaje completo pasa poco a poco frente al jugador, aprovechando al máximo el espacio de la pantalla.

### ¿Cómo lo logramos?

- El texto se escribe en **tamaño 3**, el más grande que permite una lectura cómoda.
- Cada **25 milisegundos**, el texto se recorre **4 píxeles** hacia la izquierda.
- Cuando el mensaje sale por completo de la pantalla, vuelve a aparecer por la derecha.
- Para palabras cortas, como el nombre de cada color durante el juego, el texto se muestra **fijo y centrado**, para que el jugador lo identifique al instante.
- El movimiento se controla con el reloj interno de la XIAO, de modo que el letrero puede avanzar mientras el programa sigue atento a los botones.

---

## Problemas que tuvimos y cómo los resolvimos

|Problema|Causa|Solución|
|---|---|---|
|La pantalla no mostraba nada, aunque el código se subía correctamente|Los cables SDA y SCL estaban conectados al revés|Usamos un **escáner I2C** que probaba ambas combinaciones; la pantalla apareció en la dirección 0x3C con los cables invertidos, así que los intercambiamos|
|El texto se veía muy pequeño|La pantalla de 0.96" tiene poco espacio|Letrero en movimiento con letra grande|
|La pantalla no muestra acentos ni la letra ñ|La fuente básica de la librería no incluye esos caracteres|Redactamos los mensajes sin acentos|

## Conclusión

La pantalla OLED resultó ser un componente sencillo de conectar y de programar, pero con un gran impacto en la experiencia del jugador. Lo que al principio parecía una limitación, su tamaño reducido, se convirtió en uno de los detalles más llamativos del cofre: un letrero en movimiento que le da vida y personalidad al proyecto.

![pantalla](../Media/pantalla.JPG)