<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
    <lista-vagas></lista-vagas>
    <div class="row mt-5">
      <div class="col-4">
        <indicador
          titulo="Vagas abertas"
          indicador="100"
          bg="bg-dark"
          color="text-white"
        ></indicador>
      </div>
      <div class="col-4">
        <indicador
          titulo="Profissionais cadastrados"
          indicador="225"
          bg="bg-dark"
          color="text-white"
        ></indicador>
      </div>
      <div class="col-4">
        <indicador
          titulo="Visitantes online"
          :indicador="usuariosOnline"
          bg="bg-ligth"
          color="text-dark"
        ></indicador>
        {{ usuariosOnline }}
      </div>
    </div>
  </div>
</template>

<script>
import PesquisarVaga from "@/components/comuns/PesquisarVaga.vue";
import Indicador from "@/components/comuns/Indicador.vue";
import ListaVagas from "@/components/comuns/ListaVagas.vue";

export default {
  components: { PesquisarVaga },
  name: "Home",
  components: {
    PesquisarVaga,
    Indicador,
    ListaVagas
  },
  data: () => ({
    usuariosOnline: 0,
  }),
  methods: {
    getUsuariosOnline() {
      let valor = Math.floor(Math.random() * 101); // entre 0 e 100
      this.usuariosOnline = valor;
    },
  },
  created() {
    setInterval(this.getUsuariosOnline, 1000);
  }
};
</script>

<style scoped>
</style>
