# Juego del Ahorcado (En proceso)
## Descripción
Este es un sencillo juego del ahorcado implementado en Vue.js. El objetivo del juego es adivinar una palabra oculta letra por letra antes de que se acumulen demasiados errores.

## Funcionamiento

### Juego del Ahorcado

El objetivo del juego del ahorcado es adivinar una palabra oculta letra por letra. En cada turno, el jugador selecciona una letra. El juego verifica si la letra está en la palabra oculta y actualiza el estado del juego en consecuencia.

### Estado del Juego

- **Victoria**: Si el jugador adivina todas las letras de la palabra antes de acumular demasiados errores, se muestra un mensaje de victoria. Después de mostrar el mensaje de victoria, el juego espera 5 segundos antes de reiniciarse automáticamente para dar al jugador tiempo para ver el mensaje.

- **Derrota**: Si el número de errores alcanza 6, el jugador pierde el juego. Se muestra un mensaje de derrota y, al igual que en la victoria, el juego espera 5 segundos antes de reiniciarse para que el jugador pueda ver el mensaje.

### Reinicio del Juego

El juego se puede reiniciar en cualquier momento haciendo clic en el botón "NUEVO JUEGO". Esto restablecerá el juego a su estado inicial y comenzará una nueva ronda con una nueva palabra oculta.

## Contribuciones

¡Las contribuciones son bienvenidas! Si tienes sugerencias para mejorar el juego o encuentras errores, por favor, abre un *issue* en el repositorio o envía un *pull request*. Tu ayuda es apreciada para mejorar la calidad del proyecto.

## Fotos
 ![Captura](assets/Captura de pantalla 2024-09-12 a las 18.31.43.png)
 ![Captura](ahorcado/src/assets/Captura de pantalla 2024-09-12 a las 18.32.01.png)

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
