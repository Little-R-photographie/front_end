<template>
  <b-container>
    <ul v-if="listArticles">
      <li v-for="article in listArticles" :key="article.id">
        <ArticleListComponent :article="article" />
      </li>
    </ul>
  </b-container>
</template>

<script>
import ArticleListComponent from "@/components/Blog/ArticleListComponent";
import axios from "axios";
export default {
  name: "BlogView",
  components: {
    ArticleListComponent,
  },
  data() {
    return {
      listArticles: null,
    };
  },
  methods: {
    appelListeDeToutsLesToutLesArticles() {
      axios
        .get("http://127.0.0.1:8000/api/articles")
        .then(
          (response) => (
            console.log(response.data["hydra:member"]),
            (this.listArticles = response.data["hydra:member"])
          )
        )
        .catch(function (error) {
          console.log(error);
        });
    },
  },
  mounted() {
    this.appelListeDeToutsLesToutLesArticles();
  },
};
</script>

<style scoped></style>
