<template>
  <section class="src-components-usuarios">
    <div class="jumbotron">
      <h2>Usuarios</h2>
      <hr />
      <br />

      <div v-if="usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Mail</th>
          </tr>
          <tr v-for="(usuario, i) in usuarios" :key="i">
            <td>{{ usuario.nombre }}</td>
            <td>{{ usuario.edad }}</td>
            <td>{{ usuario.email }}</td>
          </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-danger text-center">
        No se encontraron usuarios
      </h4>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-components-usuarios",
  props: [],
  mounted() {
    this.getUsuariosAxios();
  },
  data() {
    return {
      url: "https://62b708ec491a19c97aed7ab6.mockapi.io/form-TP7",
      usuarios: [],
    };
  },
  methods: {
    async getUsuariosAxios() {
      try {
        let { data } = await this.axios(this.url);
        this.usuarios = data;
      } catch (error) {
        console.error("Error Axios", error);
      }
    },
  },

  computed: {},
};
</script>

<style scoped lang="css">
</style>
