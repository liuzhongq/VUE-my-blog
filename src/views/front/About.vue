<template lang="html">
  <div class="about">
      <!--<div class="about" v-loading="loading2" element-loading-text="加载中">-->
    <div class="bg"></div>
    <div class="shows" >
     <h2>刘仲庆</h2>
      <p>一个略有强迫症的前端小菜鸟</p>
      <p><a href="https://github.com/liuzhongq" target="_blank">Github</a>&nbsp;</p>
      <h2>关于网站</h2>
      <p>本站服务端采用 Koa2 + mongoDB + nodejs 搭建, 客户端采用Vue全家桶</p>
      <p>主要功能包括: 后台登录, 注册, 管理, 标签, 文章, 支持markdown语法编辑, 支持代码高亮</p>
      <p>主要技术栈: Koa2, mongodb, vue, vue-router, vuex, axios, es6, element ui</p>
    </div>
  </div>
</template>

<script>
    export default {
        data(){
            return {
                // shows:false,
                // loading2:true
            }
        },
        // mounted(){
        //     setTimeout(()=>{
        //         this.shows = true;
        //         this.loading2 = false
        //     },100)
        // }
    }
</script>

<style lang="css" scoped>
  .bg{
    z-index:0;
    height:25rem;
    width: 100%;
    left:0;
    top:0;
    /*background-size: cover; 必须放在background-position后面用 "/" 分割*/
    background:  url('../../../dist/img/bgm.jpg') no-repeat center /cover;
    /* brightness()给图片应用一种线性乘法，使其看起来更亮或更暗。如果值是0%，图像会全黑。值是100%，
    则图像无变化。其他的值对应线性乘数效果。值超过100%也是可以的，图像会比原来更亮。如果没有设定值，默认是1。*/
    filter: brightness(1.7);
  }
    .about{
    margin:auto;
    text-align: left;
  }
  .shows{
    font-size: 1.5rem;
    line-height: 1.6em;
  }
  .about a ,.about p,.about h2{
    margin: 1rem auto 1rem 1rem;
  }
  .about h2{
    font-weight: 400;
    font-size: 2rem;
    align-self: center;
    margin-top: 1rem;
  }
</style>
