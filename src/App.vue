<template>
  <div id="app" class="container-fluid">
    <div v-if="win" class="text-center">
      <img src="@/assets/logo.png" />
    </div>
    <div v-if="lost" class="text-center">
      <img src="@/assets/perdedor.jpeg" />
    </div>

    <div class="row">
      <div class="col-sm-12">
        <h3 class="text-center text-info">JUEGO DE AHORCADO</h3>
        <ul id="horizontal-list centrado">
          <!-- Las letras en bucle por eso v-for-->
          <button v-for="(item, index) in palabra_escrita" :key="index" type="button" class="btn btn-primary cuadro text-center">
            <span class="badge">{{ item }}</span>
          </button>
        </ul>
      </div>

      <div class="container text-center">
        <div class="col-sm-12">
          <!-- El teclado -->
          <span v-for="(letra, index) in letras" :key="index">
            <button @click="comparar(letra, index)" :class="{'teclado': true, 'verde': color_botones[index] === 'verde', 'rojo': color_botones[index] === 'rojo'}">
              {{ letra }}
            </button>
          </span>
        </div>
      </div>
    </div>

    <!-- aqui la imagen del ahorcado...  -->
    <div class="row">
      <div class="col-xs-8 col-sm-8 col-md-8">
        <br />
        <div>
          <img :src="'imagenes/' + contador_errores + '.png'" alt="" />
        </div>
      </div>

      <!-- aciertos errores y nuevo juego -->
      <div class="col-xs-4 col-sm-4 col-md-4">
        <br />
        <label class="text-primary">Aciertos:</label>
        <input type="text" class="form-control text-center" v-model="contador_aciertos" />
        <br />
        <label class="text-primary">Errores:</label>
        <input type="text" class="form-control text-center" v-model="contador_errores" size="3" />
        <br />
        <button class="btn btn-primary" @click="generarAleatorio">NUEVO JUEGO</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const win = ref(false);
    const lost = ref(false);
    const contador_aciertos = ref(0);
    const contador_errores = ref(0);
    const letras = ref("ABCDEFGHIJKLMNOPQRSTUVWXYZ".split(''));
    const color_botones = ref([]);
    const palabra_escrita = ref([]);
    const palabra = ref("manzana"); // Palabra inicial
    const botones = ref([]);

    function generarAleatorio() {
      // Lógica para reiniciar el juego
      win.value = false;
      lost.value = false;
      contador_aciertos.value = 0;
      contador_errores.value = 0;
      palabra_escrita.value = Array(palabra.value.length).fill(' ');
      botones.value = Array(letras.value.length).fill(false);
      color_botones.value = Array(letras.value.length).fill('');
    }

    function comparar(letra, index) {
      if (botones.value[index]) return; // Si ya se ha pulsado, no hacer nada

      botones.value[index] = true;
      const palabraArr = palabra.value.split('');
      let found = false;

      palabraArr.forEach((char, i) => {
        if (letra.toLowerCase() === char.toLowerCase()) {
          palabra_escrita.value[i] = letra;
          contador_aciertos.value++;
          found = true;
        }
      });

      if (!found) {
        color_botones.value[index] = 'rojo';
        contador_errores.value++;
      } else {
        color_botones.value[index] = 'verde';
      }

      if (contador_aciertos.value === palabra.value.length) {
        win.value = true;
        setTimeout(() => {
      generarAleatorio();
    }, 2000);
      }

      if (contador_errores.value >= 6) {
        lost.value = true;
        setTimeout(() => {
      generarAleatorio();
    }, 2000);
      }
    }

    return {
      win,
      lost,
      contador_aciertos,
      contador_errores,
      letras,
      color_botones,
      palabra_escrita,
      generarAleatorio,
      comparar
    };
  }
}
</script>

<style scoped>
#app {
  background-color: #cecece;
  border: 4px solid green;
  border-radius: 5px;
  padding-top: 10px;
}

.teclado {
  margin-top: 5px;
  margin-left: 4px;
  width: 35px;
  display: inline-grid;
  border: 2px solid green;
  border-radius: 100px;
  background-color: #ebf5fb;
  text-align: center;
  cursor: pointer;
}

.linea {
  margin-left: 10px;
}

ul#horizontal-list {
  list-style: none;
  padding: 0;
}

ul#horizontal-list button {
  margin-left: 10px;
  width: 40px;
}

.cuadro {
  width: 30px;
  margin-left: 6px;
  text-align: center;
  padding-left: 3px;
  font-size: 1em;
  border-bottom: double;
}

.rojo {
  background-color: red;
}

.verde {
  background-color: green;
}
</style>
