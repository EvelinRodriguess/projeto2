<script setup>
import { ref } from 'vue'

const carrinhoBotao = ref(false)

const produtos = ref ([
   
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.9,
        quantidade: 1
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidade: 1
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 1
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90,
        quantidade: 1
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90,
        quantidade: 1
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90,
        quantidade: 1
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90,
        quantidade: 1
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90,
        quantidade: 1
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90,
        quantidade: 1
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 1
    }
])

const carrinho = ref({
    items: [],
    total: 0
})

function adicionarCarrinho(produto){
    carrinho.value.items.push({
        id: produto.id,
        nome: produto.nome,
        preco: produto.preco,
        quantidade: produto.quantidade,
        total: produto.preco * produto.quantidade
    });
    
}

function adicionar (index) {
    produtos.value[index].quantidade++
    const noCarrinho = carrinho.value.items.indexOf(carrinho.value.items.find( i => i.id === produtos.value[index].id))
    if (noCarrinho != -1) {
    carrinho.value.total -= carrinho.value.items[noCarrinho].total
    carrinho.value.items[noCarrinho].total = ++carrinho.value.items[noCarrinho].quantidade * carrinho.value.items[noCarrinho].preco
    carrinho.value.total += carrinho.value.items[noCarrinho].total
}
}
function diminui(index) {
  produtos.value[index].quantidade--
}
</script>

<template>

        <div v-for="(produto, index) in produtos" :key="produto.id">
    
     <div class="corpo">
        
            <p>{{ produto.id }} - {{ produto.nome }}</p>
            <br>
            <p>Preço: {{ produto.preco }}</p>
            <p>Quantidade: {{ produto.quantidade }}</p>

        <button  @click="diminui(index)">-</button>
        <button  @click="adicionar(index)">+</button>
        <button  @click="adicionarCarrinho(produto)">Adicionar</button>
        
  </div>
</div>


  <button @click="carrinhoBotao = !carrinhoBotao">Carrinho</button>

  <div v-if="carrinhoBotao">

  <div class="display-1">


    <div v-for="(produtoCarrinhos) in carrinho.items" :key="produtoCarrinhos.id">
      <h4>{{ produtoCarrinhos.id }} - {{ produtoCarrinhos.nome }} </h4>
      <p>Preço: {{ produtoCarrinhos.preco }}</p>
      <p>Quantidade de produto: {{ produtoCarrinhos.quantidade }}</p>
      <p>Valor total a pagar: {{ produtoCarrinhos.total }}</p>
      <hr>

    </div>
  </div>
</div>

</template>

<style scoped>



  .corpo {
    margin-bottom: 20px;
  }

  button {
    padding: 5px 10px;
    margin: 5px;
    border: none;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
  }

  .carrinhoBotao {
    padding: 10px;
    margin: 20px;
    border-radius: 10px;
    background-color: #007bff;
    color: #6da1e6;
    cursor: pointer;
  }

  .display-1 {
    display: flex
  }


</style>


