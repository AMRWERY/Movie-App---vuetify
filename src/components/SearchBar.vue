<template>
  <v-container fluid>
    <v-row dense>
      <v-col>
        <v-card class="mx-auto" color="teal-lighten-5" max-width="400">
          <v-card-text>
            <form @submit.prevent="searchMovies()">
              <v-text-field
                v-model="search"
                :loading="loading"
                density="compact"
                variant="solo"
                label="What are you looking for?"
                append-inner-icon="mdi-magnify"
                single-line
                hide-details
                :dense="dense"
                @click:append-inner="searchMovies()"
              ></v-text-field>
            </form>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col
      cols="12"
        xs="6"
        sm="6"
        md="4"
        lg="4"
        v-for="movie in movies"
        :key="movie.imdbID"
      >
        <router-link :to="'/movie/' + movie.imdbID">
          <v-card class="my-3 mx-3">
            <v-img :src="movie.Poster" alt="Movie Poster">
              <div class=" text-h6 text-center">
                {{ movie.Title }}
              </div>
            </v-img>
          </v-card>
        </router-link>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { ref } from "vue";
import env from "../env.js";

export default {
  name: "SearchBar",

  data() {
    return {
      loaded: false,
      loading: false,
    };
  },

  setup() {
    const search = ref("");
    const movies = ref([]);

    const searchMovies = () => {
      if (search.value != "") {
        fetch(`https://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then((response) => response.json())
          .then((data) => {
            movies.value = data.Search;
            search.value = "";
          });
      }
    };

    return {
      ph: ref(""),
      dense: ref(false),
      search,
      movies,
      searchMovies,
    };
  },
};
</script>

<style scoped>
  a {
    text-decoration: none;
  }
</style>
