<template>
  <div class="indicator-div">
    <ul>
      <li
        v-for="(_, index) in dots"
        class="dot"
        :key="index"
        :class="{ 'dot-selected': currentElementIndex === index }"
      >
        <button class="indicator-btn" @click="showCurrentElement(index)" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Indicator",
  props: {
    dots: Number,
    currentElementIndex: Number,
    showCurrentElement: Function
  }
};
</script>

<style scoped>
.indicator-div {
  margin: 0px auto;
  width: 200px;
  position: relative;
}

.indicator-div ul {
  list-style: none;
}

.indicator-div ul li {
  float: left;
  margin: 0px 10px;
}

.dot {
  height: 10px;
  width: 10px;
  border-radius: 50%;
  background: black;
  opacity: 0.2;
  cursor: pointer;
  position: relative;
}

.dot-selected {
  opacity: 0.7;
  cursor: default;
}

.indicator-btn {
  position: absolute;
  left: 0px;
  padding: 0px;
  height: 10px;
  width: 10px;
  border-radius: 50%;
  background: transparent;
  border: none;
  cursor: pointer;
}
</style>
