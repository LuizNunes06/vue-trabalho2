<script setup>

//Link do surge: "https://luiz-vue-trabalho2.surge.sh/"
const teste = ref(9999999)
import { ref } from 'vue'

const totalCarrinho = ref(0)
const validaCarrinho = ref(false)
const novoItem = ref({
    id: 0,
    nome: '',
    preco: 0,
    quantidade: 1,
    valorTotal: 0
})

const produtos = ref([
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90,
        quantidade: 0,
        valorTotal: 0
    },
    {
        id: 9,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0,
        valorTotal: 0
    }
])
const carrinho = ref([
])


function remover(index) {
    carrinho.value.splice(index, 1);
}
function decrementar(id) {
    if (produtos.value[id].quantidade > 0) {
        produtos.value[id].quantidade--;
    }
}
function adicionar(index) {

    if (produtos.value[index].quantidade > 0) {
        novoItem.value.id = produtos.value[index].id;
        novoItem.value.nome = produtos.value[index].nome;
        novoItem.value.preco = produtos.value[index].preco;
        novoItem.value.quantidade = produtos.value[index].quantidade;
        novoItem.value.valorTotal = produtos.value[index].quantidade * produtos.value[index].preco;
        totalCarrinho.value += novoItem.value.valorTotal;
        carrinho.value.push({ ...novoItem.value });
    } else {
        alert("Selecione a quantidade do produto desejado")
    }

}
function carrinhoVazio() {
    if (carrinho.value.length == 0) {
        return true
    }
}
</script>

<template>
    <div class="geral">

        <div class="produtos">
            <h1>Produtos</h1>
            <div class="gridProdutos">
                <div class="itens" v-for="(produto, index) in produtos" :key="index">
                    <p>Nome: {{ produto.nome }}</p>
                    <p>Preço: R$ {{ produto.preco }}</p>
                    <p>Quantidade: {{ produto.quantidade }}</p>
                    <p>Total: R$ {{ (produto.quantidade * produto.preco).toFixed(2) }}</p>
                    <button @click="produto.quantidade++">+</button>
                    <button @click="decrementar(produto.id - 1)">-</button>
                    <button @click="adicionar(index)">Adicionar</button>
                </div>
            </div>
        </div>

        <button v-if="validaCarrinho == false" class="btnCarrinhoUm"
            @click="validaCarrinho = !validaCarrinho">Carrinho</button>
        <div v-if="validaCarrinho" class="carrinho">
            <h2>Carrinho</h2>

            <button class="btnCarrinho" @click="validaCarrinho = !validaCarrinho">Fechar carrinho</button>
            <p class="textoCarrinho">Valor total: R$ {{ totalCarrinho.toFixed(2) }}</p>
            <p class="textoCarrinho">{{ teste }}</p>
            <div class="scrollCarrinho">
                <p v-if="carrinhoVazio()" class="msgCarrinhoVazio">Carrinho está vazio!</p>
                <div class="itens" v-for="(produto, index) in carrinho" :key="index">
                    <p>Nome: {{ produto.nome }}</p>
                    <p>Preço: R$ {{ produto.preco }}</p>
                    <p>Quantidade: {{ produto.quantidade }}</p>
                    <p>Total: R$ {{ produto.valorTotal.toFixed(2) }}</p>
                    <button @click="remover(index), totalCarrinho -= produto.valorTotal">Remover</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.btnCarrinho {
    width: max-content;
    height: max-content;
}

.btnCarrinhoUm {
    width: min-content;
    height: max-content;
    right: 10px;
    position: fixed;

}

.produtos,
.carrinho {
    text-align: center;
    margin: 20px;
    margin-top: 20px;
    width: auto;
    height: auto;
    border-radius: 6px;
    color: #F2F2F2;

}

.scrollCarrinho {
    top: 10px;
    height: 116vh;
    overflow-y: auto;
}

p {
    margin: 10px 0;
}

.textoCarrinho {
    width: max-content;
    padding: 10px;
    background-color: #262626;
    box-shadow: #262626 2px 2px 10px;
    margin: 20px auto;
    font-size: 16px;
    border-radius: 6px;
}

.msgCarrinhoVazio {
    width: max-content;
    padding: 10px;
    background-color: #6d0000;
    box-shadow: #262626 2px 2px 10px;
    margin: 20px auto;
    font-size: 16px;
    border-radius: 6px;
}

.gridProdutos {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;

}

.itens {

    width: 200px;
    padding: 10px;
    background-color: #262626;
    box-shadow: #262626 2px 2px 10px;
    margin: 20px auto;
    font-size: 16px;
    border-radius: 6px;
}


.geral {
    display: grid;
    grid-template-columns: auto auto;
}

button {
    margin: 5px;
    font-size: 17px;
    background-color: #0D0D0D;
    color: #9FA2A6;
    border-radius: 6px;
    border: none;
    padding: 10px 20px;
}

button:hover {
    transform: scale(1.02);
    transition: 0.2s;
}

h1,
h2 {
    font-size: 35px;
    padding: 10px;
    margin-top: 0;
    color: #0D0D0D;
    border-bottom: #0D0D0D solid 2px;
}</style>
