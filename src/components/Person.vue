<template>
  <div>
    <div v-if="persons.length > 0">
      <ul>
        <li v-for="person in persons" :key="person._id" id="box">
          <PersonData :compName="person.nome" :compCPF="person.cpf"/> <br>
          <CarData :compQuery="person.veiculos"/> <br>
          <DeleteBTN :compID="person._id"/>
        </li>
      </ul>
    </div>
    <div v-else>
      Carregando...
    </div>
  </div>
</template>

<script>
import PersonData from './DataCar/PersonData.vue'
import CarData from './DataCar/CarData.vue'
import DeleteBTN from './Btn/DeleteBTN.vue'

export default {
  name: 'Person',
  components: {
    PersonData,
    CarData,
    DeleteBTN,
  },
  data() {
    return {
      persons: []
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('http://localhost:8081/proprietario');
        const data = await response.json();
        this.persons = data;
      } catch (error) {
        console.error('Erro ao buscar dados:', error);
      }
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
#box {
  background-color: white; 
  margin: 10px;
  padding: 30px;
  border-radius: 10px;
}
</style>