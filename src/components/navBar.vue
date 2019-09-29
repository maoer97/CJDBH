<template>
  <!-- 头部导航 -->
  <div class="navBar">
    <ul></ul>
  </div>
</template>

<script>
  export default{
    data(){
      return{

      }
    }
  }
</script>

<style scoped lang="less">
  .navBar{
    width: 100%;
    height: 50px;
    // background: #fff;
    z-index: 1;
    position: absolute;
    top: 0;
    ul{
      float: right;
      height: 100%;
      width: 400px;
    }
  }
</style>
