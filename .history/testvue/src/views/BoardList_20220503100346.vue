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
  }
};
</script>

<style scoped>
.board { width:800px; margin: 20px auto; }
</style>