<template>
  <v-container fluid>
    <v-row dense>
      <v-col>
        <Carousel />
        <SearchBar />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Carousel from "@/layouts/Carousel.vue";
import SearchBar from "@/components/SearchBar.vue";

export default {
  name: "Home",

  components: { Carousel, SearchBar },
};
</script>
