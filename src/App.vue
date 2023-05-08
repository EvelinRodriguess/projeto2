<script setup>
import { ref } from 'vue'
const produtos = ref ('')[
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
]
const carrinho = [
    items: [
        {
            id: 1,
            nome: 'Camiseta',
            preco: 49.90,
            quantidade: 1,
            valorTotal: 49.90
        },
        {
            id: 2,
            nome: 'Calça',
            preco: 99.90,
            quantidade: 2,
            valorTotal: 199.80
        },
        {
            id: 3,
            nome: 'Meia',
            preco: 9.90,
            quantidade: 4,
            valorTotal: 39.60
        }
    ]
    total: 288.30
]
const novoItem = ref('')
function adicionar {
    produtos.value.push(novoItem.value)
    novoItem.value = ''
}
</script>

<template>
   
     <input type="text" v-model="novoItem">
     <button @click="adicionar">Adicionar</button>
  <ul>
    <div v-for="item in produtos" :key="item.id"></div>
            <p>{{ item.name }}</p>
            <p>{{ preco }}</p>

  </ul>
</template>


