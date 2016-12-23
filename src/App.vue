<template>
    <div id="list-complete-demo" class="demo">
      <div class="left">
        <div class="side">
          <div class="total">
            <label for="count_1">参与者</label>
            <textarea id="count_1" v-model="count_1" rows="9" cols="36"></textarea>
            <a  class="bt"v-on:click="inputName" title="确定">确定</a>
          </div>
        </div>
      </div>
      <div class="right">
        <div class="cont">
          <div class="num">{{ num }}</div>
          <a  class="bt" v-on:click="drawPrize" title="抽奖">抽奖</a>
          <div class="out">{{ out_name }}</div>
          <!--div class="out">胡圣喜</div-->
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      count_1: '廖德隆，林文雅，李旭辉，赵鑫晖，蔡茹芸，唐相儒，张可，龚月婴，黄爱珠，梁晓怡，王佳妮，张贝贝，周殊颖，肖遥，冯敏超，石泽远，张昶，夏玮蔚，胡圣喜，吉婉颖，刘聪，梁秋实，区诗柔，王皖莹，徐雅静，余依蕾，朱承浩，刘尧宗',
      num: 0,
      name: [],
      out_name: '？',
    }
  },
  methods: {
    drawPrize() {
      console.log(this.name.length)
      var self = this
      var interval = setInterval(() => {
        self.num = Math.floor(Math.random()*self.name.length)
      },50)
      setTimeout(() => {
        clearInterval(interval)
        var index = self.num
        self.out_name = self.name[index]
        self.name.splice(index,1)
        self.count_1 = this.name.join('，')
        console.log('中奖者: ' + self.name)
      },3000)
    },
    inputName() {
      this.name = this.count_1.split('，')
      console.log('参与者: ' + this.name)
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
.out {
  height: 40px;
  line-height: 1;
  font-size: 36px;
  margin-top: 40px;
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
  top: 40%;
  left: 50%;
  transform: translate(-50%,-50%);
}
.side {
  margin-top: -10%;
}
textarea {
  margin: 10px 0;
  outline: none;
}
.left {
  color: #fff;
  width: 300px;
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
.total .bt {
  border: 1px solid #fff;
  color: #fff;
}
.total .bt:hover{
  color: #000;
	background:#fff;
}
</style>
