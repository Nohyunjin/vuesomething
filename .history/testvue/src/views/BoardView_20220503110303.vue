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
  <div class="buttons">
	  <div class="right">
<button class="button" @click="boardListClick">목록</button>
	</div>
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
    },
    boardListClick() {
      this.$router.router.go(-1);
    }
  },
  mounted() {
    this.getBoardRead()
  },
}
</script>

<style scoped>
.board { 
  width:800px; 
  margin: 20px auto; 
}
.board table { 
  width:100%; 
  border-top:2px solid #1d4281; border-spacing:0; 
}
.board table th { 
  padding:8px 10px 10px 10px; 
  vertical-align:middle;
  color:#1d4281; 
  font-size:14px; 
  border-bottom:1px solid #ccc; 
  background:#f8f8f8;
}
.board table td { 
  padding:7px 20px 9px 20px; 
  text-align:left; 
  vertical-align:middle; 
  border-bottom:1px solid #ccc; 
  font-size:14px; 
  line-heighT:150%;
}
.board table td.title { 
  font-weight: bold; }
</style>