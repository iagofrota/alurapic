<!-- alurapic/src/App.vue -->

<template>
  <div>
    <h1>{{ titulo }}</h1>

    <img v-for="foto of fotos" :src="foto.url" :alt="foto.titulo">

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

</style>