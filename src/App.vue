<script setup>
import { ref } from 'vue'
const produtos = ref ([
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90
    }
])


const novoItem = ref([])
function adicionar {
    produtos.value.push(novoItem.value)
}
</script>

<template>
     <div class="produtos">
        <div v-for="item in produtos" :key="item.id"></div>
            <p>{{ item.name }}</p>
            <p>{{ item.preco }}</p>
     <button @click="adicionar">Adicionar</button>
  </div>
</template>

<style>
.produtos {
  display: flex;
  flex-wrap: wrap;
}

.produtos div {
  width: 200px;
  padding: 10px;
  margin: 10px;
  border: 1px solid #ccc;
}

.produtos p {
  margin: 5px 0;
}

.produtos button {
  margin-top: 10px;
  padding: 5px 10px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>


