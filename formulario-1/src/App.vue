<script setup>

import { reactive, ref } from 'vue'

const titulo = ref('Titulo')
const mostrarResultado = ref(false)
const produto = reactive({
  nome: 'Produto 1',
  preco: 19.99,
  quantidade: 10,
  categorias: []
})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h2>Formulário</h2>
      <input type="text" v-model="titulo" />
      <form @submit.prevent="mostrarResultado = !mostrarResultado">
      <div class="row">
        <label for="">Nome: </label>
        <input type="text" v-model="produto.nome">
      </div>

      <div class="row">
        <label for="">Preço: </label>
        <input type="number" step="0.01" v-model="produto.preco">
      </div>
      <div class="row">
        <label for="">Quantidade</label>
        <input type="number" v-model="produto.quantidade">
      </div>
      <button type="submit" >Mostrar</button>    
      </form>
</div>

    <div v-if="mostrarResultado" class="resultado">
      <h2>Resultado</h2>
      <p>Nome: {{ produto.nome }}</p>
      <p>Preço: {{ formatarPreco(produto.preco) }}</p>
      <p>Quantidade: {{ produto.quantidade }}</p>
      <p>Categorias: {{ produto.categorias }}</p>
      <p>{{ mostrarResultado }}</p>
    </div>

  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  gap: 1.5rem;
  width: 100vw;
  justify-content: center;
}

.formulario,
.resultado {
  border-radius: 10px;
  padding: 10px;
  width: 45%;
}

.formulario {
  background-color: rgb(120, 175, 223);
}

.resultado {
  background-color: rgb(241, 189, 239);


}

.row {
  margin: 20px 10px;
  width: 60%;
  display: flex;
  justify-content: space-between;
}


</style>
