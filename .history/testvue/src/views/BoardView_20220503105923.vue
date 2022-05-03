<template>
  <div class="board">
		<h1>This is an board view page</h1>
	</div>
</template>

<script>
export default {
  name:'BoardView',
  data() {
    return {
      boardItem : {}
    }
  },
  methods : {
    getBoardRead() {
      this.axios.get("http://localhost:9000/boards/" + this.$route.query.boardNo).then((res)=>{
        console.log(res);
        this.boardItem = res.data.data;
      }).catch((err) => {
        console.log(err);
      });
    }
  },
  mounted() {
    this.getBoardRead()
  },
}
</script>

<style>
.board {
  width : 800px;
  margin : 20px auto;
}
</style>