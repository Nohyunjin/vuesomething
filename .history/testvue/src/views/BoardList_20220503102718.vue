<template>
	<div class="board">
		<h1>This is an board list page</h1>
    <table>
			<colgroup>
				<col style="width:10%">
				<col style="width:*">
				<col style="width:15%">
				<col style="width:25%">
			</colgroup>
			<thead>
				<tr>
					<th scope="col">번호</th>
					<th scope="col">제목</th>
					<th scope="col">작성자</th>
					<th scope="col">작성일</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="boardItem in boardList" v-bind:key="boardItem.no">
					<td>{{boardItem.no}}</td>
					<td>{{boardItem.subject}}</td>
					<td>{{boardItem.writer}}</td>
					<td>{{boardItem.writedate}}</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
export default {
	name : 'BoardList',
  data : function() {
    return {
      boardList : []
    }
  },
  methods : {
	getBoardList() {
		this.axios.get("http://localhost:9000/boards").then((res)=>{
			console.log(res);
      this.boardList = res.data.data
		}).catch((err) => {
			console.log(err);
		});
	}
  },
  mounted() {
	this.getBoardList();
}
};
</script>

<style scoped>
.board { width:800px; margin: 20px auto; }
</style>