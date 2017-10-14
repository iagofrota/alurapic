<!-- alurapic/src/App.vue -->

<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotos">

        <div class="painel">
          <h2 class="painel-titulo">{{foto.titulo}}</h2>
          <div class="painel-corpo">
            <img class="imagem-responsiva" :src="foto.url" :alt="foto.titulo">
          </div>
        </div>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: 'Alurapic',
      fotos: []
    }
  },
  created() {
    // buscaremos nossas fotos aqui
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));
  }
}
</script>

<style>
.centralizado {
  text-align: center;
}

.corpo {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0 auto;
  width: 96%;
}

.lista-fotos {
  list-style: none;
}

.lista-fotos-item {
  display: inline-block;
}

.imagem-responsiva {
  width: 100%;
}
</style>