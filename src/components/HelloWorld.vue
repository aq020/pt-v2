<template>
<div>
  <div id="app" class="box">
  	    <ul class="puzzle-wrap">
            <li :class="{'puzzle': true, 'puzzle-empty': !puzzle}" v-for="(puzzle,index) in puzzles" :key="index"
             @click="moveFn(index)">
  		        <img :src="puzzle.url" />
  	        </li>
        </ul>
  		<div class="btn">
  		    <button class="btn-reset" @click="reset()">开始游戏</button>
  		</div>
  	</div>
	<div class="box1">
		<p>玩法：点击空块旁的数字方块进行移动，拼出原图</p>
	</div>
</div>
</template>
<script>
	export default {
		data() {
			return {
			    puzzles: [
          {id:0,url:require("../assets/images/vn_01.png")},
          {id:1,url:require("../assets/images/vn_02.png")},
          {id:2,url:require("../assets/images/vn_03.png")},
          {id:3,url:require("../assets/images/vn_04.png")},
          {id:4,url:require("../assets/images/vn_05.png")},
          {id:5,url:require("../assets/images/vn_06.png")},
          {id:6,url:require("../assets/images/vn_07.png")},
          {id:7,url:require("../assets/images/vn_08.png")},
    		  {id:8,url:require("../assets/images/vn_09.png")}]
			}
		},
		methods: {
			reset() {
        let parr = [
          {id:0,url:require("../assets/images/vn_01.png")},
          {id:1,url:require("../assets/images/vn_02.png")},
          {id:2,url:require("../assets/images/vn_03.png")},
          {id:3,url:require("../assets/images/vn_04.png")},
          {id:4,url:require("../assets/images/vn_05.png")},
          {id:5,url:require("../assets/images/vn_06.png")},
          {id:6,url:require("../assets/images/vn_07.png")},
          {id:7,url:require("../assets/images/vn_08.png")},""];
          parr = parr.sort(() => {
                return Math.random() - 0.5;
              });
              this.puzzles = parr;
			},
			moveFn(index) {
				let curNum = this.puzzles[index],
				    leftNum = this.puzzles[index - 1],
				    rightNum = this.puzzles[index + 1],
				    topNum = this.puzzles[index - 3],
				    bottomNum = this.puzzles[index + 3]
                if (leftNum === "") {
                    this.$set(this.puzzles,index - 1, curNum)
                    this.$set(this.puzzles,index, "")
                } else if (rightNum === "") {
                    this.$set(this.puzzles,index + 1, curNum)
                    this.$set(this.puzzles,index, "")
                } else if (topNum === "") {
                    this.$set(this.puzzles,index - 3, curNum)
                    this.$set(this.puzzles,index, "")
                } else if (bottomNum === "") {
                    this.$set(this.puzzles,index + 3, curNum)
                    this.$set(this.puzzles,index, "")
                };
            this.passFn();
			},
      passFn(){
          if(this.puzzles[0].id===0&&this.puzzles[1].id===1&&this.puzzles[2].id===2
          &&this.puzzles[3].id===3&&this.puzzles[4].id===4&&this.puzzles[5].id===5&&this.puzzles[6].id===6
          &&this.puzzles[7].id===7){
            let puzz=[
          {id:0,url:require("../assets/images/vn_01.png")},
          {id:1,url:require("../assets/images/vn_02.png")},
          {id:2,url:require("../assets/images/vn_03.png")},
          {id:3,url:require("../assets/images/vn_04.png")},
          {id:4,url:require("../assets/images/vn_05.png")},
          {id:5,url:require("../assets/images/vn_06.png")},
          {id:6,url:require("../assets/images/vn_07.png")},
          {id:7,url:require("../assets/images/vn_08.png")},
    		  {id:8,url:require("../assets/images/vn_09.png")}];
            this.puzzles = puzz
          }
      }
		}
	}
</script>
<style>
.box {
  width: 360px;
  height: 360px;
  border: 3px solid whitesmoke;
  box-shadow: 1px 1px 4px;
  margin:0px auto 0;
}
.box1 {
  width: 360px;
  height: 40px;
  border: 3px solid whitesmoke;
  box-shadow: 1px 1px 4px;
  margin: 0px auto 0;
}
.puzzle-wrap {
  display: flex;
  flex-wrap: wrap;
  width: 309px;
  height: 300px;
  margin-bottom: 40px;
  padding: 0;
  list-style: none;
  margin:20px auto 0;
}
.puzzle {
  width: 100px;
  height: 100px;
  border: 1px solid white;
}
.puzzle-empty {
  background: none;
  box-shadow: inset 0px 0px 15px;
}
 .btn {
display: flex;
justify-content: center;
}
.btn-reset {
  width: 306px;
  height: 30px;
  border: 1px solid whitesmoke;
  margin:8px auto 0;
}
</style>
