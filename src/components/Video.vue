<template>
  <div class="box">
    <video ref="videoElement" class="video" controls>
        <source src='DJI_0005.MOV' type="video/mp4">
    </video>
<!--    <button @click="playVideo">播放视频</button>-->
  </div>
</template>

<export default {
  methods: {
    // playVideo() {
    //   this.$refs.videoElement.play();
    // },
  },
};

<style lang="scss"scoped>
  .box{
    .video{
      margin-top: 60px;
      margin-left: 60px;
      width: 85%;

    }
  }
</style>
