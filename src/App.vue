<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <Topo @navegar="componente = $event" />
    <alerta v-if="exibirAlerta" :tipo="alerta.tipo" >
      <template v-slot:titulo>
        <h5>{{ alerta.titulo }}</h5>
      </template>
      <p>{{ alerta.descricao }}</p>
    </alerta>
    <Conteudo :conteudo="componente" />
  </div>
</template>

<script>
import Conteudo from "@/components/layouts/Conteudo.vue";
import Topo from "@/components/layouts/Topo.vue";
import VagasFavoritas from "@/components/comuns/VagasFavoritas.vue";
import Alerta from "@/components/comuns/Alerta.vue";

export default {
  name: "App",
  data: () => ({
    componente: "Home",
    exibirAlerta: false,
    alerta: { tipo: '', titulo: '', descricao: ''}
  }),
  components: {
    Conteudo,
    Topo,
    VagasFavoritas,
    Alerta,
  },
  methods: {
    acao(event) {
      console.log("Chegamos no componente PAI: ", event);
    },
  },
  mounted() {
    this.emitter.on("alerta", (a) => {
      this.alerta = a
      this.exibirAlerta = true;
      setTimeout(() => {
        this.exibirAlerta = false;
      }, 4000);
    });
  },
};
</script>

<style scoped>
h1 {
  color: red;
}
</style>
