<template>
  <div>
    <Formulario @adicionarPessoa="adicionarPessoa"></Formulario>
    <ul>

    


    


      <ul id="v-for-object" class="demo">
       <p>{{ this.listaPessoas.nome}}</p>
      </ul>

     



    </ul>
  </div>
</template>

<script>
import Formulario from './Formulario.vue'

export default {
  data () {
    
    return {
      listaPessoas: {
       nome: ''
      },

      items: [
      { message: 'Algo' },
      { message: 'Outro' }
    ]

   

   

      
    }
  },
  components: {
    Formulario
  },
  methods: {
    adicionarPessoa (pessoa) {
      
     this.listaPessoas.nome = pessoa.nome
    
    }
  }
}
</script>
