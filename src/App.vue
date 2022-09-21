<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async search() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>

<template>
  <main>
    <forms class="forms" @submit.prevent="search">
      <h1>Buscar CEP</h1>
      <div class="infos">
        <label for="cep">CEP</label>
        <input type="text" id="cep" v-model="cep" />
      </div>
      <button @click="search()" type="submit">buscar</button>
    </forms>
    <form class="end">
      <label for="rua">Rua</label>
      <input type="text" v-model="endereco.logradouro" />
      <label for="numero">Número</label>
      <input type="text" v-model="endereco.numero" />
      <label for="bairro">Bairro</label>
      <input type="text" v-model="endereco.bairro" />
    </form>
    {{ endereco }}
  </main>
</template>

<style>
.forms {
  border: 2px solid;
  display: flex;
  flex-direction: column;
  padding: 40px;
  width: 20%;
}
.infos {
  display: flex;
  flex-direction: column;
}
</style>
