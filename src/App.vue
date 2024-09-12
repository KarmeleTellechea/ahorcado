<template>
  <div id="app" class="container-fluid">
    <div v-if="win" class="text-center">
      <img src="imagenes/win.gif" />
    </div>
    <div v-if="lost" class="text-center">
      <img src="imagenes/lose.gif" />
    </div>

    <div class="row">
      <div class="col-sm-12">
        <h3 class="text-center text-info">JUEGO DE AHORCADO</h3>
        <ul id="horizontal-list centrado">
          <!-- Aca va la lista de las letras digitadas -->
          <button v-for="(item, index) in palabra_escrita" :key="index" type="button" class="btn btn-primary cuadro text-center">
            <span class="badge">{{item}}</span>
          </button>
        </ul>
      </div> <!-- End primera columna -->

      <div class="container text-center">
        <div class="col-sm-12">
          <!-- Aca va el teclado -->
          <span v-for="(letra, index) in letras" :key="index">
            <button @click="comparar(letra, index)" :key="index">
            {{ letra }}
            </button>
          </span>
        </div> <!-- End segunda columna -->
      </div> <!-- End container text-center -->
    </div> <!-- End row -->

    <div class="row">
      <div class="col-xs-8 col-sm-8 col-md-8">
        <br />
        <div>
          <img :src="'imagenes/' + contador_errores + '.png'" alt="" />
        </div>
      </div> <!-- End tercera columna -->

      <div class="col-xs-4 col-sm-4 col-md-4">
        <br />
        <label class="text-primary">Aciertos:</label>
        <input type="text" class="form-control text-center" v-model="contador_aciertos" />
        <br />
        <label class="text-primary">Errores:</label>
        <input type="text" class="form-control text-center" v-model="contador_errores" size="3" />
        <br />
        <button class="btn btn-primary" @click="generarAleatorio">NUEVO JUEGO</button>
      </div> <!-- End cuarta columna -->
    </div> <!-- End row -->
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      win: false,
      lost: false,
      palabra_escrita: [],  // Lista de letras adivinadas
      letras: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split(''), // Letras del teclado
      botones: [],  // Estado de los botones del teclado
      color_botones: [], // Colores de los botones del teclado
      contador_aciertos: 0,
      contador_errores: 0
    };
  },
  methods: {
  comparar(letra, index) {
    // Implement your logic here
    console.log(letra, index);
  }
}
};
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

ul#horizontal-list li {
  display: inline;
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
