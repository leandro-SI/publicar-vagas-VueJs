<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <Topo @navegar="componente = $event" />
    <Conteudo :conteudo="componente" />
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import Topo from '@/components/layouts/Topo.vue'
import VagasFavoritas from '@/components/comuns/VagasFavoritas.vue'

export default {
  name: 'App',
  data: () => ({
    componente: 'Home'
  }),
  components: {
    Conteudo,
    Topo,
    VagasFavoritas
  },
  methods: {
    acao(event) {
      console.log('Chegamos no componente PAI: ', event)
    }
  }
}
</script>

<style scoped>
h1 {
  color: red;
}
</style>
