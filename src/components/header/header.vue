<template>
 <div class="page">
     <div class="head"><img src="/static/image/zhangguangchao.png" class="avatar"></div>
     <h1>你好，我是{{resumea.name}}</h1>
     <h3>{{resumea.note}}</h3>
 </div>
</template>

<script type="text/ecmascript-6">
 export default {
     props:{
         resumea:{
             type:Object,
             default: function () {
               return { name: 'xxx',
               note:' ' 
             }}
         }
     }
 }
</script>

<style scoped lang="stylus">
.page
  text-align center
  margin 20px 0px
  .head .avatar
    width: 150px;
    height: 150px;
    margin: 0 auto;
    border-radius 75px
    background-image url(touxiang.png);
  h1
    display: block;
    font-size: 1.5rem;
    font-weight: bold;
    margin 10px
  h3 
    color: #777;
    font-weight: 400;
    margin 5px
    

 
</style>