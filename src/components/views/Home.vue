<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
    <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
      <div class="col">
        <vaga v-bind="vaga" />
      </div>
    </div>
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
import Vaga from "@/components/comuns/Vaga.vue";

export default {
  components: { PesquisarVaga },
  name: "Home",
  components: {
    PesquisarVaga,
    Indicador,
    Vaga,
  },
  data: () => ({
    usuariosOnline: 0,
    vagas: [],
  }),
  methods: {
    getUsuariosOnline() {
      let valor = Math.floor(Math.random() * 101); // entre 0 e 100
      this.usuariosOnline = valor;
    },
  },
  created() {
    setInterval(this.getUsuariosOnline, 1000);
  },
  activated () {
    this.vagas = JSON.parse(localStorage.getItem('vagas'))
  },
  mounted() {
    this.emitter.on('filtrarVagas', vaga => {

      const vagas = JSON.parse(localStorage.getItem('vagas'))
      this.vagas = vagas.filter(v => v.titulo.toLowerCase().includes(vaga.titulo.toLowerCase()))

    })
  },
};
</script>

<style scoped>
</style>
