<template>
  <div v-if="prestation && id">
    <h1>{{ prestation.nom }}</h1>
    <ul>
      <li>Nom : {{ prestation.nom }}</li>
      <li>Description : {{ prestation.description }}</li>
      <li>Prix : {{ prestation.tarif }} €</li>
      <li>Poste traitement : {{ prestation.post_traitement }}</li>
      <li>Lieux : {{ prestation.lieuDuShooting }}</li>
      <li>Durée : {{ prestation.dureeEnMinutes }} Min</li>
      <li>Lieux : {{ prestation.lieu_du_shooting }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PrestationView",

  data() {
    return {
      prestation: null,
      id: null,
    };
  },
  methods: {
    appelPrestationUnique() {
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
    this.appelPrestationUnique();
  },
};
</script>

<style scoped></style>
