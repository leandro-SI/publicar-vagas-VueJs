<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <pesquisar-vaga></pesquisar-vaga>
      </div>
    </div>
    <div class="row mt-5">
      <div class="col-4">
        <indicador titulo="Vagas abertas" indicador="100" ></indicador>
      </div>
        <div class="col-4">
        <indicador titulo="Profissionais cadastrados" indicador="225" ></indicador>
      </div>
      <div class="col-4">
        <indicador titulo="Visitantes online" indicador="25" ></indicador>
      </div>
    </div>
  </div>
</template>

<script>
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue'
import Indicador from '@/components/comuns/Indicador.vue'


export default {
  components: { PesquisarVaga },
  name: 'Home',
  components: {
    PesquisarVaga,
    Indicador
  }
}
</script>

<style scoped>

</style>
