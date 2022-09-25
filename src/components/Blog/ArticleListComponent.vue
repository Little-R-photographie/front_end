<template>
  <span v-on:click="redirectdiontPageArticle(article.id)">
    <span> {{ article.id }} </span> <br />
    <span> {{ article.titre }} </span> <br />
    <span> {{ article.contenu }} </span> <br />
    <span> {{ article.parution }} </span> <br />
  </span>
</template>

<script>
import router from "@/router";

export default {
  name: "ArticleListComponent",
  props: ["article"],
  data() {
    return {
      id: null,
    };
  },
  methods: {
    redirectdiontPageArticle(id) {
      this.id = id;
      router.push({ name: "article", params: { id: id } });
    },
  },
};
</script>

<style scoped></style>
