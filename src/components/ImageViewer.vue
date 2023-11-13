<template>
  <div class="box">
    <div class="img-container">
      <img :src="imageSrc1" alt="显示的图片1" class="img1">
      <div class="text1">威海市冬小麦空间分布图</div>
    </div>
    <div class="img-container">
      <img :src="imageSrc2" alt="显示的图片2" class="img2">
      <div class="text2">威海市玉米空间分布图</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageSrc1: '/威海市小麦空间分布图透明底.png', // 替换为你的图片路径
        imageSrc2: '/威海市玉米空间分布图透明底.png',

    };
  },
};
</script>
<style lang="scss" scoped>
    .box{
      display: flex;
      .img-container{
        position: relative;
        width: 100%;
        height:100%;
        top: -20px;
        .img1{
            position: relative;
            width: 100%;
            margin-top: 65px;
            margin-left: 20px;
        }
        .img2{
            position: relative;
            width: 100%;
            margin-top: 65px;
            margin-left: -15px;
        }
        .text1{
          position: relative;
          width: 100%;
          margin-left: 110px;
          font-size:28px;
        }
        .text2{
          position: relative;
          width: 100%;
          margin-left: 110px;
          font-size:28px;
        }
      }

    }

</style>