## Juego de memoria

La idea es simple, un juego tanto divertido y desafiante que entretenga al usuario.

La idea inicio simplemente con botones, el cofre le indicara al usuario una serie de botones al azar, los cuales tiene que presionar en la misma secuencia en la cual salgan

La secuencia del código es

1. Esperar una indicación, que un usuario interesado en jugar se acerque y presione un botón, cualquiera
2. Al recibir una señal de cualquier botón, el juego iniciara y mostrara una secuencia aleatoria de botones los cuales el usuario debe de presionar
3. Inicia el turno del jugador, el usuario debe de presionar la secuencia de botones mostrada con anterioridad

El código puede elegir de entre 5 botones distintos, estos siendo el botón verde, azul, amarillo, rosa y naranja, el juego es simple y cuenta solo con 2 niveles, cada uno con una combinación aleatoria de 3 botones, la diferencia entre el nivel 1 y el nivel 2 es la velocidad, ya que el nivel 2 muestra los botones a presionar ligeramente más rápido que el primer nivel, aumentando la dificultad en el proceso 

Sin importar el nivel, el usuario tiene 10 segundos por cada botón, si el tiempo se agota se contara como nivel no completado

Como castigo por no completar el nivel, el cofre entrara en un tiempo de cooldown por 5 segundos y regresara a la pantalla de inicio

En caso de superar el primer nivel, el juego entrara al nivel 2, en caso de superar el nivel 2, se contara como victoria y el usuario podrá recuperar su celular de dentro del cofre