<template>
  <div class="flex container">
    <table class="table">
        <tr class="header">
            <th>#</th>
            <th>Cliente</th>
            <th>Pão</th>
            <th>Carne</th>
            <th>Opcionais</th>
            <th>Ações</th>
        </tr>

        <tr v-for="pedido in pedidos" :key="pedido.id">
            <td>{{ pedido.id }}</td>
            <td>{{ pedido.nome }}</td>
            <td>{{ pedido.pao }}</td>
            <td>{{ pedido.carne }}</td>
            <td>
                <span v-for="op in pedido.opcionais" :key="op">
                {{ op }}
                </span>
            </td>
            <td>
                <select
                name="status"
                :id="'status_' + pedido.id"
                v-model="pedido.status"
                @input="Modiify(pedido.id)"
                >
                <option value="Solicitado">Selecione o status</option>
                <option value="Em andamento">Em produção</option>
                <option value="Finalizado">Finalizado</option>
                </select>
                <button class="btn" @click="Excluir(pedido.id)">Cancelar</button>
            </td>
        </tr>
    </table>
  </div>
</template>

<script>
export default {
    name : 'Dashboard',

    data() {
        return {
            pedidos : null,
            status: null
        }
    },

    methods : {
        async getPedidos() {
            const req = await fetch('http://localhost:3000/burgers')
            const data = await req.json()
            this.pedidos = data
        },

        Excluir(pedido) {
            console.log(pedido)
        },

        Modify(pedido) {
            console.log(pedido)
        }
    },

    created() {
        this.getPedidos()
    }
}
</script>

<style scoped>
    .table {
        background-color: rgb(246, 246, 246);
        border-collapse: collapse;
        text-align: center;
        padding: 20px;
        height: auto;
        width: 100%;
        font-size: 1em;
    }

    tr {
        border-bottom: 2px solid rgb(225, 224, 224);
        transform: scale(.995);
        transition: all .2s;
    }

    tr:hover {
        transform: scale(1);
    }

    .header {
        height: 60px;
        width: 100%;
        border: none;
        border-bottom: 4px solid black;
    }

    td {
        height: 70px;
        width: auto;
        max-width: 250px;
        padding: 10px;
    }

    .btn, select {
        font-size: 1em;
        width: 20%;
        height: 35px;
        padding: 5px;
        color: white;
        border: none;
        outline: non;
        border-radius: 10px;
    }

    .btn {
        background-color: red;
        margin-left: 10px;
    }

    .btn:hover {
        background-color: rgb(228, 0, 0);
    }

    select {
        width: 47%;
        border: 2px solid rgba(0, 0, 0, 0.152);
        outline: none;
        border-radius: 10px;
        color: black;
        padding: 5px 10px;
    }

    span {
        margin: 0px 5px;
    }
</style>