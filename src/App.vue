<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      resultado: {},
    };
  },
  methods: {
    async search() {
      const url = `https://www.cepaberto.com/api/v3/cep?cep=$(this.cep)`;
      this.resultado = await axios.get(url, {
        headers: {
          Authorization: "Token token=370ec793fbff3d58085a0f5f84279004",
        },
      });
    },
  },
};
</script>
<template>
  <main>
    <h1>Busca CEP</h1>
    <form @submit.prevent="search">
      <input type="text" v-model="cep" />
      <button type="submit">Buscar</button>
    </form>
    {{ resultado }}
  </main>
</template>
<style>
label {
  margin: 0%;
}

.form {
  border-radius: 5px;
}
</style>
