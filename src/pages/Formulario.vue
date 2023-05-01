<template>
    <q-form @submit.prevent="adicionarPessoa">
    
      <div>
      <q-input
      filled
      v-model="pessoa.nome"
      label="Your name *"
      hint="Name and surname"
      lazy-rules
      :rules="[ val => val && val.length > 0 || 'Iforme o nome']"
    />
  </div>

      <div>
        <q-input
        filled
        type="number"
        v-model="pessoa.idade"
        label="Your idade *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Informe a idade']"
      />
      </div>
      <button type="submit">Adicionar Pessoa</button>
    </q-form>
  </template>
  
  <script>
  export default {
    data () {
      return {
        pessoa: {
          nome: '',
          idade: ''
        }
      }
    },
    methods: {
      adicionarPessoa () {
        // Validar dados
        if (this.pessoa.nome && this.pessoa.idade) {
          // Adicionar pessoa à lista
          console.log(this.pessoa);
          this.$emit('adicionarPessoa', this.pessoa)
          // Limpar campos do formulário
          this.pessoa.nome = ''
          this.pessoa.idade = ''
        }
      }
    }
  }
  </script>
  