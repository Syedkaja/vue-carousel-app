<template>
  <div class="carousel-card">
    <arrow-component
      arrowType="left"
      v-if="this.currentElementIndex > 0 || this.loop === true"
      @click.native="previousElement"
    ></arrow-component>
    <image-component
      :imgName="currentElement.imgName"
      :mousehover="this.mousehover"
      :mouseleave="this.mouseleave"
    ></image-component>
    <arrow-component
      arrowType="right"
      v-if="this.currentElementIndex < this.images.length-1 || this.loop === true"
      @click.native="nextElement"
    ></arrow-component>
    <indicator-component
      :dots="this.images.length"
      :currentElementIndex="this.currentElementIndex"
      :showCurrentElement="this.showCurrentElement"
    />
  </div>
</template>
<script>
import Image from "./ImageCard";
import ArrowButton from "./Arrow";
import Indicator from "./Indicators";

export default {
  name: "Carousel",
  props: {
    images: Array,
    loop: Boolean,
    autoplay: Boolean,
    autoplaySpeed: Number
  },
  components: {
    "image-component": Image,
    "arrow-component": ArrowButton,
    "indicator-component": Indicator
  },
  data() {
    return {
      currentElementIndex: 0,
      timer: ""
    };
  },
  computed: {
    currentElement() {
      return this.images[this.currentElementIndex];
    }
  },
  created: function() {
    this.slide();
  },
  methods: {
    nextElement() {
      this.currentElementIndex++;
      if (this.loop) {
        if (this.currentElementIndex === this.images.length) {
          this.currentElementIndex = 0;
        }
      }
    },
    previousElement() {
      this.currentElementIndex--;
      if (this.loop) {
        if (this.currentElementIndex < 0) {
          this.currentElementIndex = this.images.length - 1;
        }
      }
    },
    showCurrentElement(elementIndex) {
      this.currentElementIndex = elementIndex;
    },
    slide() {
      if (this.autoplay) {
        if (
          this.autoplaySpeed === undefined ||
          this.autoplaySpeed === null ||
          typeof this.autoplaySpeed === String
        ) {
          this.autoplaySpeed = 2000;
        }
        this.loop = true;
        this.timer = setInterval(() => {
          this.nextElement();
        }, this.autoplaySpeed);
      } else {
        this.autoplay = false;
      }
    },
    mousehover() {
      clearInterval(this.timer);
    },
    mouseleave() {
      if (this.autoplay) {
        this.timer = setInterval(() => {
          this.nextElement();
        }, this.autoplaySpeed);
      }
    }
  }
};
</script>
<style scoped>
.carousel-card {
  position: relative;
  width: 500px;
  margin: auto;
}
</style>
