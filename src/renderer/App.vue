<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
  import apiTool from './renderUtil/api';
  import tokenUtil from './renderUtil/token';
  import errMesage from './renderUtil/errorMessage';
  import $ from 'jquery';
  export default {
    name: 'listen-now-desktop',
    mounted(){
        tokenUtil.getToken()
            .then(res => {
                let {signature, token_message} = res.data;
                token_message = token_message.substring(2, token_message.length - 1);
                apiTool.setAuth(token_message);
                tokenUtil.getExistToken(1, token_message).then(res => console.log(res));
                this.$store.dispatch('setToken', token_message);
                console.log(this.$store.state.token)
                return token_message;
            }).then(() => {
              apiTool.api.search("周传雄", apiTool.platform("网易云音乐"));
            }).catch(err => {
                console.log(err);
            });
    }
  };
</script>

<style>
  /* CSS */
  *{
    -webkit-font-smoothing:subpixel-antialiased;
    /*全局抗锯齿*/
    font-family: Helvetica, Tahoma, Arial, STXihei, "华文细黑", "Microsoft YaHei", "微软雅黑", SimSun, "宋体", Heiti, "黑体", sans-serif;
  }  
</style>
