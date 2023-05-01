<template>
  <div class="produto">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="nome"
        label="Nome"
        hint="Nome"
      />

      <q-input
      filled
      v-model="descricao"
      label="descrição"
      hint="Descrição"
    />

      <q-input
        filled
        type="number"
        v-model="quantidade"
        label="Quantidade *"
      />


      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </div>
</template>
<script>
import useQuasar from 'quasar/src/composables/use-quasar.js';
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const nome = ref(null)
    const quantidade = ref(null)
    const accept = ref(false)
    const descricao = ref(null)

    return {
      nome,
      quantidade,
      accept,
      descricao,

      onSubmit () {
        console.log(nome.value);
        console.log(descricao.value);
        console.log(quantidade.value);
      },

      onReset () {
        nome.value = null
        quantidade.value = null
      }
    }
  }
}
</script>
<style>
.produto {
  background-color:#fff; 
}
</style>
