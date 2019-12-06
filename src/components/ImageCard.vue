<template>
  <div class="image-card">
    <img :src="require(`@/assets/${imgName}`)" @mouseover="mousehover" @mouseleave="mouseleave" />
  </div>
</template>
<script>
export default {
  name: "Image",
  props: {
    imgName: String,
    mousehover: Function,
    mouseleave: Function
  }
};
</script>
