
**Proyecto:** Dopamine Trap · Cofre interactivo

---

## ¿Qué hace?

El corte láser es el proceso con el que fabricamos toda la estructura del cofre: las paredes, la base, las divisiones internas, la tapa curva y los refuerzos de las esquinas. Gracias a él, el cofre se arma únicamente por presión, sin pegamento ni materiales externos, y la tapa adopta la forma abovedada característica de un cofre pirata.

---

## Materiales y equipo

| Material / equipo            | Uso                                                        |
| ---------------------------- | ---------------------------------------------------------- |
| MDF de 6 mm y 3 mm           | Paredes, base, tapa curva y refuerzos                      |
| Cortadora láser              | Corte de todas las piezas y del patrón flexible de la tapa |
| Software de diseño vectorial | Dibujo de las piezas, uniones y patrón de kerf bending     |
| Vernier o regla              | Medición de las piezas de prueba para calcular el kerf     |

## ¿Qué es el kerf y por qué ocurre?

El **kerf** es el ancho de material que el láser elimina al cortar. El haz no es una línea perfecta sin grosor: tiene un diámetro pequeño y, además, el calor que genera vaporiza y quema una franja de material a cada lado de la trayectoria. En MDF este ancho suele estar entre **0.1 y 0.2 mm**, y depende de la máquina, del enfoque, de la potencia y del propio material.

Como consecuencia:

- Las piezas salen ligeramente **más pequeñas** que en el diseño.
- Las ranuras y los orificios salen ligeramente **más grandes**.
- Si no se toma en cuenta, las uniones quedan flojas y la caja no se sostiene por sí sola.

Este concepto lo aprendimos en la clase de Aguirre, donde también nos enseñaron a obtener el valor del kerf de forma práctica: se corta una pieza de prueba de medidas conocidas, se mide la pieza real y se compara con el diseño. La diferencia indica cuánto material retira el láser, y con ese dato se ajustan las medidas de los dientes y las ranuras antes del corte final.

---

## Ensamble de la caja

La caja se diseñó con **uniones de encaje a presión** (dientes rectos tipo rompecabezas). Al compensar el kerf en el diseño, las piezas embonan de forma justa y firme, por lo que:

- No se necesita resistol, silicón ni ningún químico para unir la estructura.
- La caja puede armarse y desarmarse para dar mantenimiento a la electrónica.
- Las uniones quedan alineadas y la caja conserva su forma aun al agitarla.

Elegimos este método porque en las clases de Proyecto de Ingeniería trabajamos ampliamente con corte láser, por lo que ya conocíamos cómo diseñar uniones que embonaran correctamente, considerando el kerf, el tipo de material y su grosor.

---

## Kerf bending: la tapa curva

### ¿Cómo funciona?

El **kerf bending** consiste en cortar un patrón de líneas paralelas e interrumpidas sobre el material. Las pequeñas franjas de MDF que quedan entre los cortes actúan como bisagras diminutas: cada una se tuerce un poco y, en conjunto, permiten que una lámina rígida se doble en curva sin romperse. Funciona de manera similar al caparazón de un armadillo, que es rígido por segmentos pero flexible en su conjunto.

El comportamiento del patrón depende principalmente de dos factores:

- **Separación entre líneas:** a menor separación, la pieza es más flexible, pero también más frágil.
- **Profundidad y limpieza del corte** (potencia, velocidad y número de pasadas): si el corte es insuficiente, la pieza no dobla; si es excesivo, el material se quema y pierde resistencia.

### Proceso de pruebas

Llegar al patrón final requirió varias muestras. Cada intento nos ayudó a entender el equilibrio entre flexibilidad y resistencia.

|Intento|Cambio realizado|Resultado|Aprendizaje|
|---|---|---|---|
|1|Separación de 6 mm entre líneas|El corte fue insuficiente; la pieza no se podía doblar|Con tanta separación, el material conserva casi toda su rigidez|
|2|Más potencia y más pasadas|El láser prácticamente consumió la madera; la muestra quedó muy quemada y se rompía al mínimo contacto|El exceso de pasadas debilita y carboniza el MDF|
|3|Líneas más gruesas, variando la separación en milímetros|La pieza fue muy flexible, pero demasiado débil|Más flexibilidad no siempre es mejor: la tapa debe soportar uso|
|4|Ajuste de capas y pasadas|Por fuera se veía perfecta, pero en realidad casi no era flexible|El grosor del MDF exige suficientes pasadas para que el corte atraviese bien|
|5|Parámetros finales (ver tabla siguiente)|Cortes limpios, sin quemaduras, flexible y resistente|Muestra aprobada para la tapa del cofre|

### Parámetros finales

|Parámetro|Valor|
|---|---|
|Pasadas con separación de 5 mm|2|
|Pasada final con separación de 3 mm|1|
|Potencia|85 / 75|
|Velocidad|12|

Con esta configuración, la madera no se quema, los cortes quedan limpios y la pieza es lo bastante flexible para formar la curva de la tapa sin volverse frágil ni desprenderse.

---

## Bordes decorativos funcionales

Además de la estructura, utilizamos la cortadora láser para fabricar los **refuerzos decorativos de las esquinas**. Aunque su diseño aporta el aspecto de un cofre pirata, también cumplen una función técnica: el sistema que detecta si la tapa está abierta o cerrada utiliza tiras de aluminio cuyos cables se fijan con tornillos. Para ello se necesitaba una base sólida y más gruesa que la pared de 3 mm, y estos refuerzos la proporcionan. De esta forma, la decoración también forma parte del funcionamiento del cofre.

---

## Problemas que tuvimos y cómo los resolvimos

|Problema|Causa|Solución|
|---|---|---|
|La tapa no se doblaba|Separación entre líneas demasiado amplia|Reducir la separación y ajustar el número de pasadas|
|La muestra se quemaba y se rompía|Exceso de potencia y de pasadas|Disminuir las pasadas y ajustar potencia y velocidad|
|Muestra flexible pero débil|Líneas demasiado gruesas o demasiado juntas|Buscar un punto intermedio entre separación y resistencia|
|Muestra aparentemente correcta pero rígida|El corte no atravesaba lo suficiente el grosor del material|Ajustar capas y pasadas hasta lograr un corte completo|
|Uniones de la caja flojas|El láser retira material (kerf)|Medir el kerf con piezas de prueba y compensarlo en el diseño|

## Conclusión

El corte láser nos permitió construir un cofre resistente, preciso y fácil de ensamblar, sin depender de adhesivos. La tapa curva fue el mayor reto de fabricación: requirió cinco muestras hasta encontrar el balance adecuado entre flexibilidad y resistencia. Este proceso nos enseñó que el kerf no es solo un detalle técnico, sino un factor que define si una pieza embona, si se dobla y si resiste el uso.

#### Muestras del proceso de bending

![Muestras](Media/laser1.JPG)


#### Muestra del proceso del bending final, ya el prototipo con medidas

![MuestraGrande](Media/laser2.JPG)