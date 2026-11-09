
# DOPAMINE TRAP
Cofre Interactivo: Desafíos y Bloqueo por Retos

**Equipo:** Danae Hernandez Saavedra, Leonardo, Jose Pedro Itzcoatl Macuil

## Problema

La adicción digital y las plataformas de videos cortos han reconfigurado por completo la atención de las nuevas generaciones, friéndoles literalmente el cerebro con estímulos constantes de dopamina rápida. Hoy en día, los niños y adolescentes han normalizado pasar horas scrolleando sin parar, al punto de que les cuesta mantenerse desconectados incluso para comer, bañarse, dormir o ir al baño.

Este consumo desmedido no es solo un mal hábito temporal; como señalan Fung, Rojas y Delgado (2020), el tiempo excesivo de pantalla genera un impacto profundo en la salud integral de la infancia y la adolescencia. El problema va mucho más allá del sedentarismo, los retrasos en el habla, los estragos psicológicos, sociales o el aumento de peso.

A nivel físico y cognitivo, la situación es crítica:

- **Daño visual irreversible:** Taverne (2022) y Castro et al. (2022) advierten que el uso desproporcionado de dispositivos desgasta la salud ocular, provocando fatiga, resequedad y el constante rascado de ojos. Peor aún,cuando esto ocurre a una edad temprana, el globo ocular se adapta asumiendo que la pantalla es el punto focal de distancia, lo que hace que el ojo crezca de más de forma anómala, desencadenando miopía severa o empeorando los problemas visuales preexistentes (Mendieta Pineda, 2017).

- **Déficit de atención:** La sobreestimulación constante destruye la capacidad de enfoque profundo. Como documenta Castre Campero (2020), el uso descontrolado de pantallas en infantes genera cuadros directos de déficit de atención,volviéndolos incapaces de tolerar el aburrimiento o procesar información que no se mueva a la velocidad de un algoritmo.


En conclusión, la problemática que enfrentamos se basa en:

- Dependencia severa a los estímulos de dopamina rápida generada por las plataformas de video corto y redes sociales.

- Sedentarismo profundo y resistencia absoluta a despegarse del celular en actividades cotidianas básicas.

- Deterioro cognitivo crítico, marcado por la aparición de déficit de atención.

- Daños físicos graves y de carácter irreversible en el desarrollo visual, destacando la inducción y aceleración de la miopía infantil.

## Usuario

La problemática afecta  a toda la población, pero impacta de forma crítica en niños y jóvenes.

## Sensa / Responde

- Qué mide y con qué sensor

    - **Proximidad:** Sensor ultrasónico (HC-SR04) para detectar cuando el usuario se acerca al cofre.
    
    - **Movimiento / Inclinación:** Acelerómetro (MPU6050) para medir si el cofre es agitado de lado a lado (derecha/izquierda) o levantado (salto).
    
    - **Sonido / Volumen:** Micrófono (MAX9814) para medir los decibeles cuando el usuario grita o canta en los retos de voz.
    
    - **Cámara:** (ESP32-CAM) Captura una foto para validar el reto de postura y permitir la apertura o guardar evidencia del fallo.
    
	- **Interacción física:** Matriz de 5 botones de colores tipo pop-it / arcade para los retos de secuencia táctil.


- Qué hace al medir (LED, buzzer, servo, pantalla)

    
    - **Pantalla OLED (en los dientes):** Muestra el quiz inicial, los retos activos, la cuenta regresiva del cooldown o mensajes de advertencia.
        
    - **Ojos LED RGB:** Cambian a **Verde** al superar un reto con éxito (permitiendo que el cofre se abra); cambian a **Rojo**y parpadean al fallar o activar un bloqueo (cooldown).
        
    - **Servomotor (SG90):** Bloquea o libera automáticamente la tapa del cofre pirata según el estado del juego y los aciertos.
        
    - **Buzzer:** Emite melodías de victoria (tipo cofre legendario) o tonos de error y penalización.


## Fabricación

**Estructura y Chasis en Corte Láser (MDF 3mm)**

El cuerpo del cofre se arma con piezas cortadas en láser usando paneles de MDF y un sistema de encaje a presión (_press-fit_ o ensamble):

- **Cuerpo base y uniones:** Las paredes y divisiones se ensamblan como rompecabezas con dientes rectos. Este paso lo tenemos súper dominado y nos da muchísima confianza porque ya lo aplicamos y calculamos a la perfección (incluyendo el kerf) en nuestro proyecto pasado de la caja, obvio volveremos a hacer unas pruebas solo para ver que todo siga igual.

- **Tapa curva:** Como el cofre de Fortnite es abovedado arriba, usaremos cortes flexibles en la madera (_kerf bending_) para que pueda doblarse sin romperse y formar la curva exacta, esto es algo que apenas estuvimos viendo que se puede hacer, es como el caparazón de un armadillo por decirlo de una manera.

- **Espacio interno:** Un doble fondo para esconder todos los cables, las tarjetas XIAO ESP32-C6 y mantener todo ordenado por dentro, para que cuando agiten y así no se mueva todo.


**Piezas Impresas en 3D (Detalles, Mecánica y Forma)**

Como el láser es plano, la impresión 3D nos sirve para darle volumen, estilo y la forma real del cofre de Fortnite:

- **Esquineros y herrajes:** Las piezas de las esquinas con relieve de remaches para que parezca un cofre de verdad y tape las uniones de la madera.

- **Candado y pestillo:** El candado del frente se imprime en 3D y se conecta directo al motor para trabar y destrabar la tapa automáticamente.

- **Botones:** Las carcasas para los 5 botones de colores que el usuario va a presionar en los retos.

- **Gemas y luces:** Piezas con plástico transparente para que los LEDs brillen kawaii en la parte frontal y den el efecto de cofre legendario.

- **Soportes para sensores:** Bases a la medida para acomodar la cámara (ESP32-CAM) y el sensor de distancia sin que desentonen con el diseño.


**Conclusión de fabricación**

Se puede resumir en que usamos el corte láser para armar toda la caja rápido y con buena estructura, y dejamos la impresión 3D para los detalles que necesitan resistencia (como los botones y el seguro) y los adornos visuales.

## Nivel

Hard mode, obvio porque amamos los desafíos y confiamos plenamente en que podemos materializar este proyecto con éxito absoluto. Ir por este nivel no es solo cumplir con la rúbrica, sino la oportunidad perfecta para aprender nuevas disciplinas; como equipo sabemos que adquirir el mayor número de habilidades a lo largo de la carrera es clave, ya que dominar un poco de todo hace mucho más fácil llevar cualquier idea de la mente a las manos. Además, crecimos viendo a Jorge el Curioso y las genialidades del Laboratorio de Dexter, así que traemos esa chispa de científicos e ingenieros locos listos para construir lo que sea.

## Declaración de uso de IA

**Qué herramienta usamos:** 

Gemini y Claude

**Para qué la ocupamos:**

- Para redactar y estructurar la propuesta de manera clara, expresando nuestras ideas con la mayor precisión y formalidad técnica posible.

- Para resumir artículos y documentos académicos encontrados en internet (como Google Scholar), ahorrándonos horas de lectura pesada de PDFs largos y yendo directo a la información clave.

- Para organizar la planeación del diseño del cofre, ayudándonos a definir qué componentes electrónicos llevaría, cotizar costos aproximados y elegir los modelos adecuados.

- Para rebotar ideas y resolver dudas de ingeniería sobre cómo materializar lo que teníamos en la cabeza (por ejemplo,cómo calcular y aplicar el corte flexible o _kerf bending_ en el MDF para lograr la tapa abovedada del cofre).


## Citas
Aunque el formato de la entrega no requería formalmente un apartado de bibliografía, nos pareció fundamental incluir las fuentes consultadas. Entender una problemática desde su raíz  nos permitió diseñar una solución con verdadero impacto y sustento real.


- **Fung, M. P., Rojas, M. E. J., & Delgado, C. L. G. (2020). Impacto del tiempo de pantalla en la salud de niños y adolescentes. Revista Médica Sinergia, 5(06), 1-10.**
    
    Analiza de forma integral cómo el consumo excesivo dedispositivos afecta la salud física, social y psicológica en la infancia y la adolescencia.
    
- **Taverne, M. (2022). Efectos de las pantallas sobre la visión humana: posibles daños irreparables y consecuencias psico-fisiológicas.**
    
    Aborda los daños oculares directos, el desgaste visual y las secuelas psico-fisiológicas derivadas del uso continuo de tecnología.
    
- **Castro, L. P., Pérez, P. C., Deustua, S. S., & Martínez, M. D. L. G. (2022). Horas pantallas y miopía en niños. Revista Cubana de Oftalmología, 35(1).**
    
    Examina la relación directa entre la cantidad de horas frente a las pantallas y el desarrollo o empeoramiento de la miopía infantil.
    
- **Mendieta Pineda, Z. L. (2017). Efectos adversos en el desarrollo visual y cognitivo en niños menores de 3 años relacionados con el tiempo excesivo de uso de pantallas digitales.**
    
    Destaca cómo la sobreexposición temprana altera el desarrollo visual normal (haciendo que el ojo se adapte a distancias falsas y crezca de forma anómala) y cognitivo.
    
- **Castre Campero, S. (2020). Déficit de atención causado por el uso excesivo de dispositivos electrónicos en infantes de 5 a 7 años de la Urb. Las brisas en Pueblo Libre.**
    
    Documenta la aparición de cuadros de déficit de atención provocados por la sobreestimulación digital y la incapacidad de procesar ritmos lentos.
