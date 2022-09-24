<template>
  <b-container>
    <ul class="cards">
      <li v-for="prestation in listPrestations" :key="prestation.id">
        <prestationCard :prestation="prestation" />
      </li>
    </ul>
  </b-container>
</template>

<script>
import axios from "axios";
import prestationCard from "@/components/prestation/PrestationCard";
export default {
  name: "PrestationComponent",
  components: {
    prestationCard,
  },
  data() {
    return {
      listPrestations: [],
    };
  },
  methods: {
    appelListeDeToutesLesPrestations() {
      axios
        .get("http://127.0.0.1:8000/api/prestations")
        .then(
          (response) => (this.listPrestations = response.data["hydra:member"])
        )
        .catch(function (error) {
          console.log(error);
        });
    },
  },
  mounted() {
    this.appelListeDeToutesLesPrestations();
  },
};
</script>

<style scoped>
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin: 4rem 5vw;
  padding: 0;
  list-style-type: none;
}
</style>
