<template>
  <div class="main">
    <nav-bar></nav-bar>
    <!-- <cesium-ball></cesium-ball> -->
    <div class="leftBoxL">
      <div class="leftBoxOne"></div>
    </div>
    <div class="rightBoxL"></div>
  </div>
</template>

<script>
  import CesiumBall from '@/components/cesiumBall.vue'
  import NavBar from '@/components/navBar.vue'
  export default{
    data(){
      return{

      }
    },
    components:{
      CesiumBall,NavBar
    }
  }
</script>

<style scoped lang="less">
  *{
    padding: 0;
    margin: 0;
  }
  .main{
    position: relative;
    width: 100%;
    height: 100%;
    background: url(../../assets/img/bg.png)no-repeat;
    .leftBoxL{
      height: 918px;
      width: 370px;
      position: absolute;
      background: url(../../assets/img/leftLineBox.png)no-repeat;
      left: 20px;
      top: 94px;
      .leftBoxOne{

      }
    }
    .rightBoxL{
      width:415px;
      height: 918px;
      background: url(../../assets/img/rightLineBox.png)no-repeat right;
      position: absolute;
      right: 20px;
      top: 94px;
    }
  }
</style>
