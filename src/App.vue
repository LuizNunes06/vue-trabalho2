<script setup>
//import { ref } from 'vue'

const produtos = [
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


function remover(index) {
    carrinho.value.splice(index, 1)
  }
</script>

<template>
    <div class="geral">

        <div class="produtos">
            <ul>
                <li class="itens"  v-for="(produto, index) in produtos" :key="index">
                    <p>Nome: {{ produto.nome }}</p>
                    <p>Preço: {{ produto.preco }}</p>
                    <p>Quantidade: {{ produto.quantidade }}</p>
                </li>
            </ul>
        </div>

        <div class="carrinho">
            <ul>
                <li class="itens" v-for="(item, index) in carrinho" :key="index">
                    <p>Nome: {{ item.nome }}</p>
                    <p>Preço: {{ item.preco }}</p>
                    <p>Quantidade: {{ item.quantidade }}</p>
                    <button @click="remover(index)">Remover</button>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
.itens {
    width: 200px;
    padding: 10px;
    background-color: rgb(87, 87, 87);
    margin: 50px;
}

p {
    color: aliceblue;
}

.abaAdicionar {
    margin: 50px;
    padding: 20px;
    width: 200px;
    background-color: rgb(0, 59, 0);
}

li {
    list-style: none;
}

.geral {
    display: grid;
    grid-template-columns: 50% 50%;
}
</style>
