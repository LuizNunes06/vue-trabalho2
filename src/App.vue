<script setup>
import { ref } from 'vue'


const produtos = ref([
    {
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 0
    },
    {
        nome: 'Calça',
        preco: 99.90,
        quantidade: 0
    },
    {
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0
    },
    {
        nome: 'Sapato',
        preco: 199.90,
        quantidade: 0
    },
    {
        nome: 'Boné',
        preco: 29.90,
        quantidade: 0
    },
    {
        nome: 'Óculos',
        preco: 99.90,
        quantidade: 0
    },
    {
        nome: 'Relógio',
        preco: 299.90,
        quantidade: 0
    },
    {
        nome: 'Bermuda',
        preco: 79.90,
        quantidade: 0
    },
    {
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0
    }
])
const carrinho = ref([
    {
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 1,
        valorTotal: 49.90
    },
    {
        nome: 'Calça',
        preco: 99.90,
        quantidade: 2,
        valorTotal: 199.80
    },
    {
        nome: 'Meia',
        preco: 9.90,
        quantidade: 4,
        valorTotal: 39.60
    }
])


function remover(index) {
    carrinho.value.splice(index, 1)
  }
  

</script>

<template>
    <div class="geral">

        <div class="produtos">
            <h1>Produtos</h1>
            <div class="gridProdutos">
                <div class="itens"  v-for="(produto, index) in produtos" :key="index">
                    <p>Nome: {{ produto.nome }}</p>
                    <p>Preço: {{ produto.preco }}</p>
                    <button @click="adicionar">Adicionar</button>
                </div>
            </div>
        </div>
        

        <div class="carrinho">
            <h2>Carrinho</h2>
                <div class="itens" v-for="(item, index) in carrinho" :key="index">
                    <p>Nome: {{ item.nome }}</p>
                    <p>Preço: {{ item.preco }}</p>
                    <button @click="remover(index)">Remover</button>
                    <hr>

                </div>
        </div>
    </div>
</template>

<style scoped>

.produtos,.carrinho{
    text-align: center;
    margin: 20px;
    margin-top: 0px;
    width: auto;
    height: min-content;
    background-color: #404040;
    border-radius: 6px;
    color: #F2F2F2;
}
.gridProdutos{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    
}

.itens {
    width: 200px;
    padding: 10px;
    background-color: #262626;
    border-radius: 6px;
    box-shadow: #262626 2px 2px 10px;
    margin: 20px auto;
    font-size: 16px;
}


.geral {
    display: grid;
    grid-template-columns: 70% 30%;
}
button{
    font-size: 17px;
    background-color: #0D0D0D;
    color: #9FA2A6;
    border-radius: 6px;
    border: none;
    padding: 10px 20px;
}
button:hover{
    transform: scale(1.02);
    transition: 0.2s;
}

h1,h2{
    font-size: 35px;
    padding: 10px;
    margin-top: 0;
    background-color: #262626;
    border-bottom: #0D0D0D solid 2px;
}
</style>
