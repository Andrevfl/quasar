<template>
    <div class="ba">
        <div class="Logo">
            <img src="..//img/logo_Credsystem_branco.png" alt="Logo">
        </div>
        <div class="button-container">
            <div>
            <q-btn @click="mostrarComponente = !mostrarComponente"  color="white" text-color="black" label="Produto" />
        </div>
            <q-btn @click="estoque = !estoque"  color="primary" text-color="black" label="Estoque" />
            <q-btn color="secondary" label="Caixa" />
          </div>
          <div class="container">
            <meu-componente v-if="mostrarComponente" />
            <estoque v-if="estoque" />
          </div>
         
    </div>
</template>
  
<script>
import MeuComponente from './/produto.vue'
import estoque from './/estoque.vue'
import caixa from './/caixa.vue'


export default {
  components: {
    MeuComponente,
    estoque,
    caixa

  },
  data() {
    return {
      mostrarComponente: false,
      estoque: false,
      caixa: false
    }
  }
}
</script>

<style>
.ba {
    background-color: #007aff;
    height: 120px;
    border-radius: 3px;
    margin-top: 2px;
    margin-left: 2px;
    margin-right: 2px;
}

.button-container {
  margin-top: 15px;
    display:flex;
    gap: 20px;
  }

  .button {
    padding: 10px;
  }

  .container {
    margin-top: 20px;
    width : 1322px;
    margin-right: 2px;
    height: 500px;
    background-color:#2D2B30;
    
  }








</style>
  