<template>
  <div class="home">
    <PrestationComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import PrestationComponent from "@/components/PrestationComponent";

export default {
  name: "HomeView",
  components: {
    PrestationComponent,
  },
};
</script>
