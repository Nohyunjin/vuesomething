<template>
	<div class="board">
		<h1>This is an board list page</h1>
	</div>
</template>

<script>
export default {
	name : 'BoardList',
  data() {
    return {
      boardList :[]
    }
  },
  methods : {
	getBoardList() {
		this.axios.get("http://localhost:9000/boards").then((res)=>{
			console.log(res);
		}).catch((err) => {
			console.log(err);
		});
	}
}
};
</script>

<style scoped>
.board { width:800px; margin: 20px auto; }
</style>