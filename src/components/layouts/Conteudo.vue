<template>
  <div>
    <h1>{{titulo}}</h1>
    <button @click="conteudo = 'home'" >Home</button>
    <button @click="conteudo = 'publicar-vaga'" >Publicar Vaga</button>
    <!-- renderizar de modo dinâmico os componentes home e publicar-vaga -->
    <!-- <home></home>
    <publicar-vaga></publicar-vaga> -->
    <component :is="conteudo" ></component>
  </div>
</template>

<script>
import Home from '@/components/views/Home.vue'
import PublicarVaga from '@/components/views/PublicarVaga.vue'

export default {
  name: 'Conteudo',
  components: {
    Home,
    PublicarVaga
  },
  data: () => ({
    teste: 'O componente foi criado',
    titulo: 'Componente Conteúdo',
    conteudo: 'home'
  }),
  methods: {

  }
}
</script>

<style scoped>
h1 {
  color: black;
}
</style>
