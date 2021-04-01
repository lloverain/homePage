<template>
  <div id="app">
    <el-container>
      <el-main>
      <a class="textstyle">{{text}}</a>
      <sendform></sendform>
        </el-main>
    </el-container>
  </div>
</template>

<script>
import sendform from "./components/sendform.vue";
import axios from 'axios';
export default {
  name: "App",
  components: {
    sendform,
  },
  data() {
    return {
      url: "https://v1.hitokoto.cn/?max_length=20", //api接口
      text: ""
    };
  },
  created() {
    this.getdata();
  },
  methods: {
    getdata() {
      var that = this;
      axios.get(this.url).then((res) => {
        that.text = res.data.hitokoto;
      });
    },
  },
};
</script>

<style>
html,body{
margin: 0px;
padding: 0px;
width: 100%;
height: 100%;  
}
#app{
/* background-image:transparent url(); */
margin: 0px;
padding: 0px;
width: 100%;
height: 100%;
}

#app::before{
   content:'';
    position:absolute;
    top:0;
    left:0;
    width: 100%;
    height: 100%;
    background:transparent url('https://rain-1256608339.cos.ap-chengdu.myqcloud.com/wallhaven-pkkm6p.png') center center no-repeat;
    background-size: 100%;
    filter:blur(3px);
    z-index:-1;
    background-size:cover;
}

.el-header, .el-footer {
  text-align: center;
  line-height: 100px;
}

.el-aside {
  text-align: center;
  line-height: 200px;
}

.el-main {
   position: absolute;
    left: 50%;
    top:30%;
    transform: translate(-50%,-50%);
  text-align: center;
  line-height: 100px;
}


.textstyle{
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
  font-size: 20px;
  color: rgb(255, 255, 255);
}
</style>
