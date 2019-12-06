<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Carousel :images="images" :loop="true" :autoplay="true" :autoplaySpeed="2000" />
  </div>
</template>

<script>
// @ is an alias to /src
import Carousel from "@/components/Carousel.vue";

export default {
  name: "Home",
  components: {
    Carousel
  },
  data() {
    return {
      images: [
        {
          imgName: "brazil.jpg"
        },
        {
          imgName: "hawaii.jpg"
        },
        {
          imgName: "jamaica.jpg"
        },
        {
          imgName: "panama.jpg"
        }
      ]
    };
  }
};
</script>
