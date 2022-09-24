<template>
  <div>
    <h1>{{ prestation.nom }}</h1>
    <ul>
      <li>Id : {{ prestation.id }}</li>
      <li>Nom : {{ prestation.nom }}</li>
      <li>Description : {{ prestation.description }}</li>
      <li>Prix : {{ prestation.prix }} €</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PrestationView",

  data() {
    return {
      prestation: "",
      id: "",
    };
  },
  methods: {
    appelPrestationUniqu() {
      axios
        .get(`http://127.0.0.1:8000/api/prestations/+${this.$route.params.id}`)
        .then((response) => (this.prestation = response.data))
        .catch(function (error) {
          console.log(error);
        });
    },
    idDynamique() {
      this.id = this.$route.params.id;
    },
  },
  mounted() {
    this.idDynamique();
    this.appelPrestationUniqu();
  },
};
</script>

<style scoped></style>
