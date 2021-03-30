<template>
  <div>
    <div class="sendform">
        <el-input
    :placeholder="text"
    v-model="form.name"
    size="medium"
    class="input-with-select"
    @keyup.enter="search"
  >
    <template #prepend>
      <el-select v-model="select"  :placeholder="select" style="width:100px">
        <el-option label="百度" selected value="1"></el-option>
        <el-option label="google" value="2"></el-option>
        <el-option label="搜狗" value="3"></el-option>
      </el-select>
    </template>
    <template #append>
      <el-button icon="el-icon-search" @click="search"></el-button>
    </template>
  </el-input>
    </div>
   
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "sendform",
  data() {
    return {
      url: "https://v1.hitokoto.cn/?max_length=20", //api接口
      text: "",
      select:"1",
      form: {
        name: "",
      },
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
    search(){
      console.log('test')
      var that = this;
      console.log(that.select)
      if(that.select==1){
        //百度
        window.location.href = 'https://www.baidu.com/s?wd='+that.form.name
      }else if(that.select==2){
        //google
        window.location.href = 'https://www.google.com.hk/search?q='+that.form.name
      }else if(that.select==3){
        //搜狗
         window.location.href = 'https://www.sogou.com/web?query='+that.form.name
      }


    }
  },
};
</script>

<style scoped>
.sendform{
  width:500px;
}
 .el-select .el-input {
    width: 130px;
  }
  .input-with-select .el-input-group__prepend {
    background-color: #fff;
  }
</style>
