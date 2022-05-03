<template>
  <div class="board">
		<h1>This is an board view page</h1>
    <table>
			<colgroup>
				<col style="width:18.5%">
				<col style="width:">
			</colgroup>
			<tbody>
				<tr>
					<th scope="row">제목</th>
					<td class="title">{{boardItem.subject}}</td>
				</tr>
				<tr>
					<th scope="row">내용</th>
					<td>{{boardItem.content}}</td>
				</tr>
				<tr>
					<th scope="row">작성자</th>
					<td>{{boardItem.writer}}</td>
				</tr>
				<tr>
					<th scope="row">작성일자</th>
					<td>{{boardItem.writedate}}</td>
				</tr>
			</tbody>
		</table>
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