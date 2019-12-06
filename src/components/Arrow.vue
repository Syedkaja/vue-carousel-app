<template>
  <div class="arrow-div">
    <button class="btn" v-bind:class="arrowType">
      <img class="icon" :src="require(`@/assets/${arrowType}.png`)" />
    </button>
  </div>
</template>
<script>
export default {
  name: "ArrowButton",
  props: {
    arrowType: String
  }
};
</script>
<style scoped>
.arrow-div .btn {
  width: 35px;
}

.arrow-div .btn.left {
  position: absolute;
  left: -20px;
  top: 128px;
}

.arrow-div .btn.right {
  position: absolute;
  right: -20px;
  top: 128px;
}

.arrow-div .btn img {
  width: 30px;
  height: 25px;
  margin-left: -4px;
}
</style>
