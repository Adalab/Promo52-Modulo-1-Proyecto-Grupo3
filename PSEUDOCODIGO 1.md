INICIO DEL JUEGO

1.  **Inicialización de datos:**
    * Crear una LISTA `lista_palabras_pc` de DICCIONARIOS:
        * Cada diccionario contendrá una `palabra` (clave) y su `pista` (valor).
        * Ejemplo: `[{"manzana": "Fruta roja"}, {"python": "Lenguaje de programación"}]`
    * Crear un DICCIONARIO `vidas_ahorcado`:
        * Las claves serán el número de vidas restantes (ej: 6, 5, 4, ...)
        * Los valores serán los dibujos ASCII correspondientes al ahorcado en ese estado.
        * Ejemplo (como se definió anteriormente).
    * Crear un DICCIONARIO `mensajes_animacion`:
        * Las claves serán números de intentos (ej: 2, 4, 6, ...)
        * Los valores serán los mensajes de ánimo o advertencia.
        * Ejemplo: `{2: "¡Vamos, tú puedes!", 4: "¡Cuidado, estás cerca!"}`
    * Crear un SET `letras_usadas` para almacenar las letras ingresadas en cada partida.
    * Inicializar VARIABLES:
        * `numero_jugadores`
        * `nombre_jugador1`
        * `nombre_jugador2`
        * `palabra_secreta`
        * `pista_actual`
        * `vidas_restantes`
        * `letras_correctas` (para la palabra adivinada, inicialmente con guiones bajos)
        * `puntaje_jugador1`
        * `puntaje_jugador2`
        * `partidas_ganadas_jugador1`
        * `partidas_ganadas_jugador2`
        * `turno_jugador_elige` (para rastrear quién elige la palabra en modo 2 jugadores, inicializado en 1)
        * `seguir_jugando` (booleano para controlar si se juegan más partidas)

2.  **Solicitar número de jugadores:**
    * Preguntar al usuario cuántos jugadores serán (1 o 2).
    * Guardar la respuesta en `numero_jugadores`.

3.  **Saludar y obtener nombres:**
    * Si `numero_jugadores` es 1:
        * Saludar al jugador.
        * Asignar "PC" como el oponente.
        * Solicitar el nombre del jugador y guardar en `nombre_jugador1`.
    * Si `numero_jugadores` es 2:
        * Saludar a ambos jugadores.
        * Solicitar el nombre del Jugador 1 y guardar en `nombre_jugador1`.
        * Solicitar el nombre del Jugador 2 y guardar en `nombre_jugador2`.
        * Informar que inicialmente `nombre_jugador1` elegirá la palabra y `nombre_jugador2` adivinará.

4.  **Bucle principal del juego (mientras `seguir_jugando` sea Verdadero):**
    * **Preparación de la partida:**
        * Limpiar el SET `letras_usadas` usando `letras_usadas.clear()`.
        * Reiniciar `vidas_restantes` al valor inicial (ej: 6).
        * Si `numero_jugadores` es 1:
            * Seleccionar una palabra y su pista aleatoriamente de `lista_palabras_pc`.
            * Asignar la palabra a `palabra_secreta` y la pista a `pista_actual`.
        * Si `numero_jugadores` es 2:
            * Si `turno_jugador_elige` es 1:
                * Solicitar a `nombre_jugador1` que ingrese la `palabra_secreta`.
                * Solicitar a `nombre_jugador1` que ingrese una `pista_actual` para `nombre_jugador2`.
            * Si `turno_jugador_elige` es 2:
                * Solicitar a `nombre_jugador2` que ingrese la `palabra_secreta`.
                * Solicitar a `nombre_jugador2` que ingrese una `pista_actual` para `nombre_jugador1`.
            * Invertir el `turno_jugador_elige` (si era 1 ahora es 2, si era 2 ahora es 1).
        * Crear `letras_correctas` como una lista de guiones bajos (`_`) con la misma longitud que `palabra_secreta`.
        * Mostrar la longitud de la `palabra_secreta`.
        * Mostrar la `pista_actual`.
        * Mostrar el dibujo inicial del ahorcado usando `vidas_ahorcado[vidas_restantes]`.

    * **Bucle de adivinanzas (mientras `vidas_restantes` > 0 y la palabra no ha sido adivinada):**
        * Determinar el jugador actual:
            * Si `numero_jugadores` es 1, el jugador actual es `nombre_jugador1`.
            * Si `numero_jugadores` es 2:
                * Si `turno_jugador_elige` era 2 en la preparación, el jugador actual es `nombre_jugador1`.
                * Si `turno_jugador_elige` era 1 en la preparación, el jugador actual es `nombre_jugador2`.
        * Solicitar al jugador actual que ingrese una letra o la palabra "pista".
        * Convertir la entrada del jugador a minúscula.
        * Si la entrada es igual a "pista":
            * Mostrar la `pista_actual`.
        * Sino:
            * Si la entrada tiene una longitud de 1 (es una letra):
                * Si la letra ya fue usada (está en `letras_usadas`):
                    * Informar al jugador que ya ingresó esa letra.
                * Si la letra no fue usada:
                    * Agregar la letra a `letras_usadas`.
                    * Si la letra está en `palabra_secreta`:
                        * Actualizar `letras_correctas` reemplazando los guiones bajos en las posiciones correctas.
                        * Informar al jugador que acertó una letra.
                    * Si la letra no está en `palabra_secreta`:
                        * Decrementar `vidas_restantes` en 1.
                        * Mostrar el dibujo del ahorcado usando `vidas_ahorcado[vidas_restantes]`.
                        * Mostrar un mensaje de error (opcionalmente, usar mensajes de `mensajes_animacion`).
                    * Mostrar las letras usadas hasta el momento.
                    * Mostrar el estado actual de la palabra (`letras_correctas`).
                    * Si todas las letras en `letras_correctas` coinciden con `palabra_secreta`:
                        * El jugador actual ha ganado la partida.
                        * Incrementar el contador de partidas ganadas del jugador (y su puntaje si lo implementas).
                        * Salir del bucle de adivinanzas.
            * Sino (si la entrada no es "pista" y no tiene longitud 1):
                * Informar al jugador que la entrada no es válida.
        * Si `vidas_restantes` llega a 0:
            * El jugador actual ha perdido la partida.
            * Mostrar la `palabra_secreta`.
            * Informar al jugador que ha perdido.

    * **Fin de la partida:**
        * Preguntar a los jugadores si quieren jugar otra partida.
        * Si responden "no", establecer `seguir_jugando` a Falso.

5.  **Final del juego:**
    * Si `numero_jugadores` es 2:
        * Determinar el ganador final por número de partidas ganadas (y por puntaje en caso de empate).
        * Mostrar el resultado final.
    * Si `numero_jugadores` es 1:
        * Mostrar un mensaje de agradecimiento por jugar.

FIN DEL JUEGO
