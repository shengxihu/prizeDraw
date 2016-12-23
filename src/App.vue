<template>
    <div id="list-complete-demo" class="demo">
      <div class="left">
        <div class="side">
          <div class="total">
            <label for="count_1">参与总人数</label>
            <input id="count_1" v-model="count_1">
          </div>
          <div class="out">
            <label for="count_2">中奖人数</label>
            <input id="count_2" v-model="count_2">
          </div>
        </div>
      </div>
      <div class="right">
        <div class="cont">
          <div class="num">{{ num }}</div>
          <a  class="bt" v-on:click="drawPrize" title="抽奖">抽奖</a>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      count_1: 0,
      count_2: 0,
      num: 0,
      arr: [],
    }
  },
  methods: {
    randomIndex: function () {
      return Math.floor(Math.random() * this.count_1+1)
    },
    drawPrize() {
      var self = this
      var interval = setInterval(() => {
        self.num = self.randomIndex()
      },100)
      setTimeout(() => {
        var flag = self.arr.indexOf(self.num)
        if(flag == -1) {
          clearInterval(interval)
          self.arr.push(self.num)
          console.log(self.arr)
        } else {
          self.drawPrize()
        }
      },3000)
    }
  }
}
</script>

<style>
html,body,.demo {
  width: 100%;
  height: 100%;
}
body {
  margin: 0;
}
.num {
  width: 50px;
  font-size: 36px;
}
.bt,.num {
  vertical-align: middle;
  display: inline-block;
  height: 36px;
  line-height: 36px;
}
.side, .cont {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
.side {
  margin-top: -10%;
}
input {
  margin: 10px 0;
  outline: none;
}
.left {
  color: #fff;
  width: 200px;
  height: 100%;
  float: left;
  position: relative;
  background: #377d6a;
}
.right {
  position: relative;
  overflow: hidden;
  margin-left: 200px;
  height: 100%;
}
.bt {
	display: inline-block;
  text-decoration: none;
  cursor: pointer;
  border: 1px solid #377d6a;
  border-radius: 3px;
  width: 122px;
  margin-left: 20px;
  color: #000;
  padding: 0;
  outline: none;
  overflow: hidden;
  line-height: 36px;
  animation-fill-mode: backwards;
}
.bt:hover{
  color: #fff;
	background:#377d6a;
	transition: all .3s ease-out;
}
</style>
