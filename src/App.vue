<template>
  <div>
    <h1>Componente App</h1>
    <Topo @nomeDoEventoQueSeraCapturadoNoPai="acao($event)" />
    <Conteudo />
  </div>
</template>

<script>
import Conteudo from '@/components/layouts/Conteudo.vue'
import Topo from '@/components/layouts/Topo.vue'

export default {
  name: 'App',
  components: {
    Conteudo,
    Topo
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
