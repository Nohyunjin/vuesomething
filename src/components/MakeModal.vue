<template>
  <div class = "black-bg" v-if="openModal == true">
    <div class = "white-bg">
      <img :src="data[index].image">
      <h4>{{ data[index].title }}</h4>
      <p>가격 : {{ data[index].price }}원</p>
      <p>{{ data[index].content }}</p>
      <button @click="$emit('openModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name : "MakeModal",

  props : {
    data : Array,
    index : Number,
    openModal : Boolean,
  },

}
</script>

<style>

</style>