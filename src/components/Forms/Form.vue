<template>
    <div>
        <form @submit.prevent="enviarFormulario" method="post" id="box">
            <br>
            <input type="text" v-model="nome" placeholder="Nome"/> <br>
            <input type="text" v-model="cpf" placeholder="CPF"/> <br>
            <br><br>
            <input type="text" v-model="placa" placeholder="Placa"/> <br>
            <input type="text" v-model.number="ano" placeholder="Ano"/> <br>
            <input type="text" v-model.number="mensalidade" placeholder="Mensalidade"/> <br>
            <button type="button" @click="addCar">Adicionar Carro</button>
            <br><br>
            <router-link to="/"><button type="submit">Enviar</button></router-link>
        </form>
        <div v-for="veiculo in veiculos" :key="veiculo._id" id="box">
            <p>Carro: </p>
            <p>{{ veiculo.placa}}</p>
            <p>{{ veiculo.ano}}</p>
            <p>{{ veiculo.mensalidade}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Form',
    data() {
        return {
            nome: "",
            cpf: "",
            placa: "",
            ano: "",
            mensalidade: "",
            veiculos: [],
            json: ""
        }
    },
    methods: {
        addCar() {
            const veiculo = {
                placa: this.placa,
                ano: Number(this.ano),
                mensalidade: Number(this.mensalidade)
            };

            this.veiculos.push(veiculo);

            this.placa = "";
            this.ano = "";
            this.mensalidade = "";

            console.log(this.veiculos);
        },
        enviarFormulario() {
            const nome = this.nome;
            const cpf = this.cpf;
            const veiculos = this.veiculos;
            const data = { nome, cpf, veiculos };

            fetch('http://localhost:8081/proprietario', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(data)
            })
            .then(response => response.json())
            .then(data => {
                console.log('Success:', data);
                this.json = JSON.stringify(data, null, 2);
            })
            .catch((error) => {
                console.error('Error:', error);
            });
        }
    }
}
</script>

<style>
body {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: black;
}
ul {
    list-style-type: none;
}

</style>

<style scoped>
#box {
  background-color: white; 
  margin: 10px;
  padding: 10px;
  border-radius: 10px;
}
</style>