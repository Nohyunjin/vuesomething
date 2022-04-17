<template>
  <div class = "black-bg" v-if="openModal == true">
    <div class = "white-bg">
      <img :src="data[index].image">
      <h4>{{ data[index].title }}</h4>
      <p>{{ data[index].content }}</p>
      <!--<input @input="month = $event.target.value">-->
      <input v-model="month">
      <p>{{ month }}개월 가격 : {{ data[index].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name : "MakeModal",
  data(){
    return{
      month : 1,
    }
  },
  watch : {
    month(a){
      if (isNaN(a) == true) {
        alert('문자 입력하지마세요');
        this.month = 1;
      }
    },
  },
  props : {
    data : Array,
    index : Number,
    openModal : Boolean,
  },

}
</script>

<style>

</style>