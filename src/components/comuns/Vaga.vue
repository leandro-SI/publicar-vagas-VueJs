<template>
  <div class="card">
    <div class="card-header bg-dark text-white">
      <div class="row">
        <div class="col d-flex justify-content-between">
          <div>
            {{ titulo }}
          </div>
          <div>
            <div class="form-check form-switch">
              <input type="checkbox" class="form-check-input" v-model="favoritada">
              <label for="" class="form-check-label">Favoritar</label>
            </div>
          </div>
        </div>
      </div>

    </div>
    <div class="card-body">
      <p>{{ descricao }}</p>
    </div>
    <div class="card-footer">
      <small class="tetx-muted">
        Salário: R$ {{ salario }} | Modalidade: {{ getModalidade }} | Tipo: {{ getTipo }} | Publicação: {{ getPublicacao }}
      </small>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Vaga',
  data: () => ({
    favoritada: false
  }),
  props: {
    titulo: {
      type: String,
      required: true,
      validator(p) {
        if (p, p.length < 6) return false
        return true
      }
    },
    descricao: {
      type: String,
      default: 'O contratante não adicionou uma descrição para esta vaga'
    },
    salario: {
      type: [Number, String],
      required: true
    },
    modalidade: {
      type: String,
      required: true
    },
    tipo: {
      type: String,
      required: true
    },
    publicacao: {
      type: String,
      required: true
    }
  },
  methods: {

  },
  computed: {
    getModalidade() {
      switch(this.modalidade) { 
        case '1': return 'Home Office'
        case '2': return 'Presencial'
      }
      return ''
    },
    getTipo() {
      switch(this.modalidade) { 
        case '1': return 'CLT'
        case '2': return 'PJ'
      }
      return ''
    },
    getPublicacao() {
      let dataPublicacao = new Date(this.publicacao)
      //return dataPublicacao.toLocaleString('pt-BR')
      return dataPublicacao.toLocaleDateString('pt-BR')
    }
  },
  watch: {
    favoritada(valorNovo) {
      if (valorNovo) {
        this.emitter.emit('favoritarVaga', this.titulo)
      } else {
        this.emitter.emit('desfavoritarVaga', this.titulo)
      }
    }
  }
};
</script>