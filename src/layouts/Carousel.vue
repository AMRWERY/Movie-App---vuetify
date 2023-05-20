<template>
  <v-carousel cycle height="400" hide-delimiter-background show-arrows="hover">
    <v-carousel-item
      v-for="slide in slides"
      :key="slide"
      :src="slide.img"
      cover
    ></v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "Carousel",

  data() {
    return {
      slides: [
        { img: "https://justfields.com/storage/projects/7M5rV059/153259.jpg" },
        { img: "https://justfields.com/storage/projects/7M5rV059/17350.webp" },
        { img: "https://justfields.com/storage/projects/7M5rV059/1084875.jpg" },
        {
          img: "https://justfields.com/storage/projects/7M5rV059/desktop-wallpaper-naruto-poster-naruto-2021.jpg",
        },
      ],
    };
  },
};
</script>
