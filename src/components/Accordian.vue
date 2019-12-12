<template>
  <div>
    <div class="accordian" v-for="(cdata, index) in collapsibleData" :key="index">
      <div class="panel-heading" @click="showAnswer(index)">{{cdata.question}}</div>
      <div class="panel-body" :class="{ active: cdata.active }">{{cdata.answer}}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Accordian",
  props: {
    collapsibleData: Array,
    showAll: Boolean
  },
  //   isActive: Boolean,
  //   data() {
  //     return {
  //       isActive: false
  //     };
  //   },
  methods: {
    showAnswer(index) {
      //   if (index !== null || index !== undefined) {
      //     for (let i = 0; i < this.collapsibleData.length; i++) {
      //       if (index === i) {
      //         this.isActive = index;
      //       }
      //     }
      //   }
      this.collapsibleData[index].active = !this.collapsibleData[index].active;
      if (!this.showAll) {
        for (let i = 0; i < this.collapsibleData.length; i++) {
          if (index !== i) {
            this.collapsibleData[i].active = false;
          }
        }
      }
    }
  }
};
</script>
<style scoped>
.accordian {
  position: relative;
  width: 500px;
  margin: auto;
  display: block;
  background-color: #d2d2d2;
  padding: 10px;
  text-align: left;
}
.accordian .panel-heading {
  background-color: #009999;
  padding: 5px;
  color: #fff;
  font-weight: 500;
  cursor: pointer;
}
.accordian .panel-body {
  background-color: #ffffff;
  padding: 5px;
  color: #000;
  font-weight: 500;
  display: none;
}

.active.panel-body {
  display: block;
}
</style>
