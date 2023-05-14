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
    carrinho.value.total += produto.preco * produto.quantidade
}

function aumentarQuantidade (index) {
    produtos.value[index].quantidade++
    const pos = carrinho.value.items.indexOf(carrinho.value.items.find( i => i.id === produtos.value[index].id))
    if (pos != -1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total = ++carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
    carrinho.value.total += carrinho.value.items[pos].total
}
}
function diminuiQuantidade(index) {
  produtos.value[index].quantidade--
}


 function removerProdutoCarrinho(produto) {
  const index = carrinho.value.items.findIndex(item => item.id === produto.id);
  if (index !== -1) {
    const removido = carrinho.value.items.splice(index, 1)[0];
    carrinho.value.total -= removido.total;
  }
}

</script>

<template>

        <div v-for="(produto, index) in produtos" :key="produto.id">
    
     <div class="produto">
        
            <p>{{ produto.id }} - {{ produto.nome }}</p>
            <br>
            <p>Preço: {{ produto.preco }}</p>
            <p>Quantidade: {{ produto.quantidade }}</p>

        <button type="button" class="cor1" @click="diminuiQuantidade(index)">-</button>
        <button type="button" class="cor1" @click="aumentarQuantidade(index)">+</button>
        <button type="button" class="cor2" @click="adicionarCarrinho(produto)" >Adicionar</button>
        
        
  </div>
</div>


  <button type="button" class="cor1" @click="carrinhoBotao = !carrinhoBotao">Ver carrinho</button>

  <div v-if="carrinhoBotao">

  <div class="carrinho">

    <div v-if="carrinhoBotao" class="carrinho"></div>
    <div v-for="(produtoCarrinhos) in carrinho.items" :key="produtoCarrinhos.id">
      <h4>{{ produtoCarrinhos.id }} - {{ produtoCarrinhos.nome }} </h4>
      <p>Preço: {{ produtoCarrinhos.preco }}</p>
      <p>Quantidade de produto: {{ produtoCarrinhos.quantidade }}</p>
      <p>Valor total a pagar: {{ produtoCarrinhos.total }}</p>
      <button type="button" class="cor3" @click="() => removerProdutoCarrinho(produtoCarrinhos)">Remover</button>
      <hr>

    </div>
  </div>
</div>

</template>

<style scoped>

  .produto {
    margin-bottom: 20px;
    border-bottom: 3px solid cornflowerblue;
    padding: 10px;
  }

  p{
  font-family: 'Courier New', Courier, monospace;
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
    margin: 5px;
    border-radius: 5px;
    background-color: #2970bb;
    color: #000000;
    cursor: pointer;
  }

  .carrinho {
    font-family: 'Courier New', Courier, monospace;
    display: flex
  
  }

  .cor1{
    background-color: rgb(153, 210, 233);
    color: rgb(0, 0, 0);
  }

 .cor2{
  background-color: #09e93a;
  color: black;
}

 .cor3{
  background-color: red;
}

</style>


