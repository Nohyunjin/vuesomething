<template>

  <MakeModal @closeModal="openModal = false" :data="data" :index="index" :openModal="openModal"/>

  <div class = "nav-bar">
    <a v-for = "(m, i) in menus " :key="i">{{ m }}</a>
  </div>
  <div>
    <button @click="sortPriceAsc">낮은 가격순</button>
    <button @click="sortPriceDesc">높은 가격순</button>
    <button @click="sortName">이름순</button>
    <button @click="rollBack">되돌리기</button>
  </div>
  <MakeList @openModal="openModal = true" :data="data[i]" v-for="(a,i) in data" :key="a"/>

</template>

<script>
import data from '../src/assets/data/data.js'

import MakeModal from '../src/components/MakeModal.vue'
import MakeList from '../src/components/MakeList.vue'

export default {
  name: 'App',

  data(){
    return{
      menus : ["Home", "Rooms", "About"],
      openModal : false,
      data : data,
      index : 0,
      dataOrigin : [...data],
    }
  },

  components: {
    MakeModal,
    MakeList,
  },

  methods: {
    sortPriceAsc(){
      this.data.sort(function(a,b){
        return a.price - b.price;
      })
    },
    sortPriceDesc(){
      this.data.sort(function(a,b){
        return b.price - a.price;
      })
    },
    rollBack(){
      this.data = [...this.dataOrigin];
    },
    sortName(){
      this.data.sort(function(a,b){
        return a.title.localeCompare(b.title);
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.nav-bar {
  background-color: cadetblue;
  padding: 15px;
  border-radius: 5px;
}

.nav-bar a{
  color: aliceblue;
  padding : 10px;
}

body{
  margin : 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding : 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img{
  width: 60%;
}

.start {
  opacity: 0;
  transition: all 1s;

}
.end {
  opacity: 1;
}

</style>
