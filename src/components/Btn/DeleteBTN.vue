<<template>
  <button @click="deletarUsuario">Deletar Usuário</button>
</template>

<script>
export default {
  name: 'DeleteBTN',
  props: {
    compID: {
      type: String,
      required: true
    }
  },
  methods: {
    async deletarUsuario() {
      try {
        console.log(this.compID)
        const response = await fetch(`http://localhost:8081/proprietario/${this.compID}`, {
          method: 'DELETE'
        });
        if (response.ok) {
          console.log(`Usuário ${this.compID} deletado com sucesso.`);
        } else {
          console.error(`Erro ao deletar usuário ${this.compID}: ${response.statusText}`);
        }
      } catch (error) {
        console.error(`Erro ao deletar usuário ${this.compID}: ${error.message}`);
      }
    }
  }
}
</script>
