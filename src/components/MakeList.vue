<template>
  <img :src="data.image" class="room-img">
  <h3 @click="$emit('openModal', data.id)">{{ data.title }}</h3>
  <p>가격 : {{ data.price }}원</p>
</template>

<script>
export default {
  name : "MakeList",

  props : {
    data : Array,
  }

}
</script>

<style>

</style>