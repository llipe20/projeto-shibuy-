<template>
    <Modal :msg="msg" v-show="msg"/>
    <div>
        <div class="main">
            <form action="" class="form" @submit="newPedido">

                <!-- INPUT DE NOME -->
                <div class="box-input">
                    <label for="nome">Cliente: </label>
                    <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite seu nome">
                </div>

                <!-- SELECT DOS PAES -->
                <div class="box-input">
                    <label for="pao">Escolha o pão: </label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="null">Selecione o pão</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                    </select>
                </div>

                <!-- SELECT DAS CARNES -->
                <div class="box-input">
                    <label for="carne">Escolha a carne: </label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="null">Selecione a carne</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                    </select>
                </div>

                <!-- INPUT OPCIONAIS -->
                <div class="box-input">
                    <label for="opcionais">Escolha os opcionais: </label>

                    <div class="box-list">
                        <div v-for="option in opctionsData" :key="option.id"  class="check-box">
                            <input type="checkbox" name="opcionais" id="opcionais"  v-model="opcionais" :value="option.tipo">
                            <span>{{ option.tipo }}</span>
                        </div>
                    </div>
                </div>

                <!-- BOTÃO CONFIRMAR -->
                <div class="box-input">
                    <input type="submit" class="botton-enviar" value="Finalizar pedido">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import Modal from '../components/Modal.vue'

export default {
    name : "Form",

    components : {
        Modal
    },

    data() {
        return {
            nome : null,
            pao : null,
            carne : null,
            opcionais : [],
            carnes : null,
            paes : null,
            opctionsData : null,
            msg : null
        }
    },
    
    methods : {
        async getCardapio() {
            const req = await fetch('http://localhost:3000/ingredientes') 
            const data = await req.json()

            this.carnes = data.carnes
            this.paes = data.paes
            this.opctionsData = data.opcionais
        },

        // Método para adicionar pedidos
        async newPedido(e) {

            // Passo 1: Pegar os dados do pedido
            e.preventDefault()

            const pedido = {
                nome : this.nome,
                carne : this.carne,
                pao : this.pao,
                opcionais : Array.from(this.opcionais),
                status : "Solicitado"
            }

            // Passo 2: Inserir no banco os dados
            const dataJson = JSON.stringify(pedido)
            const req = await fetch('http://localhost:3000/burgers', {
                method : 'POST',
                headers : {'Content-Type' : 'application/json'},
                body : dataJson
            })
            const resposta = await req.json()
            console.log(resposta)

            // Passo 3: Notificar usuário
            this.msg = 'Pedido realizado com sucesso!'

            // Passo 4: Limpar os campos
            this.nome = null,
            this.pao = null,
            this.carne = null,
            this.opcionais = null
            setTimeout(() => this.msg = null, 2000)
        }
    },

    mounted() {
        this.getCardapio()
    }
}
</script>

<style scoped>
    .form, .main {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        height: auto;
        gap: 30px;
    }

    .main {
        align-items: center;
        width: 100%;
        padding: 10px;
    }

    label {
        font-size: 1.15em;
        border-left: 5px solid yellow;
        padding: 5px 10px;
    }

    span {
        font-size: 1.15em;
    }

    .box-input, .check-box {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .check-box {
        flex-direction: row;
        gap: 5px;
    }

    .check-box input {
        height: 20px;
        width: 20px;
    }

    .box-list {
        display: flex;
        flex-wrap: wrap;
        width: 30vw;
        gap: 25px 25px;
    }

    input, select {
        font-size: 1.15em;
        width: 30vw;
        height: 40px;
        border: 2px solid rgba(0, 0, 0, 0.152);
        outline: none;
        color: rgba(255, 255, 255, 0.575);
        border-radius: 10px;
        color: black;
        padding: 5px 10px;
    }

    .botton-enviar {
        background-color: green;
        color: white;
        height: 50px;
        border: none;
        outline: none;
    }

    .botton-enviar:hover {
        background-color: rgb(1, 110, 1);
    }
</style>