<template>
    <button class="botao botao-perigo" :type="tipo" @click="disparaAcao()">{{rotulo}}</button>
</template>
<script>
export default {
  props: ["tipo", "rotulo", "confirmacao"],
  methods: {
    disparaAcao() {
      console.log(typeof this.confirmacao);

      if (this.confirmacao) {
        if (confirm("Confirma operacao?")) {
          this.$emit("botaoAtivado");
        }
        return;
      }
      this.$emit("botaoAtivado");
    }
  }
};
</script>    

<style scoped>
.botao {
  display: inline-block;
  padding: 10px;
  border-radius: 3px;
  margin: 10px;
  font-size: 1.2em;
}

.botao-perigo {
  background: firebrick;
  color: white;
}

.botao-padrao {
  background: darkcyan;
  color: white;
}
</style>