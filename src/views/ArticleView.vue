<template>
  <div v-if="article && id">
    <h1>{{ article.titre }}</h1>
    <ul>
      <li>Id : {{ article.id }}</li>
      <li>Titre : {{ article.titre }}</li>
      <li>Contenu : {{ article.contenu }}</li>
      <li>Parrution : {{ article.parrution }} €</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "ArticleView",
  data() {
    return {
      article: null,
      id: null,
    };
  },
  methods: {
    appelarticleUnique() {
      axios
        .get(`http://127.0.0.1:8000/api/articles/${this.$route.params.id}`)
        .then((response) => (this.article = response.data))
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
    this.appelarticleUnique();
  },
};
</script>

<style scoped></style>
