<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Carousel :images="images" :loop="true" :autoplay="true" :autoplaySpeed="2000" />
    <Accordian :collapsibleData="accordianData" :showAll="false" />
  </div>
</template>

<script>
// @ is an alias to /src
import Carousel from "@/components/Carousel.vue";
import Accordian from "@/components/Accordian.vue";

export default {
  name: "Home",
  components: {
    Carousel,
    Accordian
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
      ],
      accordianData: [
        {
          question: "Some Question1",
          answer: "Anwser for the above question1",
          active: false
        },
        {
          question: "Some Question2",
          answer: "Anwser for the above question2",
          active: false
        },
        {
          question: "Some Question3",
          answer: "Anwser for the above question3",
          active: false
        },
        {
          question: "Some Question4",
          answer: "Anwser for the above question4",
          active: false
        }
      ]
    };
  }
};
</script>
