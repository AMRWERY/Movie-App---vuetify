<template>
  <v-container fluid class="text-center">
    <v-row dense>
      <v-col>
        <h1 class="text-red">{{ movie.Title }}</h1>
        <br>
        <h5>{{ movie.Year }}</h5>
        <br>
        <v-img :src="movie.Poster" class="img" />
        <br />
        <p>{{ movie.Plot }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "../env.js";

export default {
  name: "MovieDetails",

  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `https://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          movie.value = data;
        });
    });

    return {
      movie,
    };
  },
};
</script>

<style scoped>
.img {
  display: block;
  max-width: 250px;
  margin-bottom: 16px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 12px;
}
</style>

