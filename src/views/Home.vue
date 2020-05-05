<template>
  <div class="home">
    <div class="video">
      <video src="../assets/movie/video-me-desktop.mp4"></video>
    </div>
    <div class="section"></div>
  </div>
</template>

<script>
export default {

  name: 'Home',
  mounted() {
    // Pour lancer la video des que la vue est monter :)
    // document.querySelector('video').play();
  },

};
</script>

<style lang="scss">
  @import '../css/style';

  .home{
    overflow-x: hidden;
    .video{
      width: 100vw;
      height: 100vh;
      background: $black;
      video {
        width: 100vw;
        height: 100%;
      }
    }
    .section {
      height: 100vh;
      width: 100vw;
      background: $homeGrey;
    }
  }
</style>
