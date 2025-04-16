# PROYECTO1-GRUPO3 - JUEGO DEL AHORCADO

Este proyecto es un juego del Ahorcado en Python. Puedes jugar sola o con otra persona.

## Cómo jugar 🎲 

1.  Asegúrate de tener Python instalado.
2.  Ejecuta el archivo del juego.

### Una jugadora  🍺

* El ordenador elige una palabra secreta y te da una pista.
* Intenta adivinar la palabra letra por letra.
* Si aciertas, la letra se muestra.
* Si fallas, pierdes una vida. Tienes 10 vidas.
* Si quieres una pista, escribe `pista`.
* Al final, verás cuántas palabras has adivinado.

### Dos jugadoras 🍻 

* La Jugadora 1 escribe una palabra secreta y una pista para la Jugadora 2.
* La Jugadora 2 intenta adivinar la palabra.
* Luego, la Jugadora 2 escribe una palabra y una pista para la Jugadora 1.
* Se lleva la cuenta de los puntos según los fallos al adivinar.
* Gana quien adivine más palabras. Si hay empate en palabras adivinadas, gana quien tenga menos puntos (menos fallos en total).
* También se puede pedir pista escribiendo `pista`.

## Partes del código 💻

* **Diccionarios:**  📓
    * `dic_random_words`: Palabras para adivinar con sus pistas.
    * `dicc_motivation`: Mensajes que aparecen al fallar.
    * `ahorcado_pics`: Dibujos del ahorcado según las vidas que quedan.
      
* **Funciones:**  🎤
  
    * `basic_game()`: La función principal del juego. Calcula puntos por fallos.
    * `min_letters_word()`: Comprueba que la palabra tenga al menos dos letras.
    * `min_letters_hint()`: Comprueba que la pista tenga al menos dos letras.

## Para mejorar ⤴️

* Se podrían añadir más palabras.
* Se podría mostrar la puntuación total al final de la partida de una jugadora.

¡Gracias por jugar!
