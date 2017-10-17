<template>
 <div class="page">
<h2>{{name}}</h2>
<div class="line"></div>
 </div>
</template>

<script type="text/ecmascript-6">
 export default {
   props:['name']
 }
</script>

<style scoped lang="stylus">
.page
  position relative 
  h2
    position relative 
    font-size: 1.25rem
    margin 10px 0px 30px 0px
    font-weight 500
  .line
        display block
        position absolute
        left 0
        bottom -30px
        border-top 1px solid #ddd
        width 100%
        margin 20px 0px 
 
</style>
