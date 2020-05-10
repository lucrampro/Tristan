<template>
  <div class="home">
    <div class="video">
      <video src="../assets/movie/video-me-desktop.mp4"></video>
    </div>
    <div class="section">
      <div class="wrapper">
        <img class="tristan" src="../assets/img/home/tristan.png" alt="">
      </div>
      <div class="wrapper">
        <p class="subtitle">Creative developer</p>
        <p>
          Depuis plus de 7 ans, j’aime mettre ma créativité et mon expertise
          au service de vos projets…
        </p>
        <div class="wrapper--icons">
          <img src="../assets/img/home/first-section/glasses.png" alt="" srcset="">
          <img src="../assets/img/home/first-section/cafe.png" alt="" srcset="">
          <img src="../assets/img/home/first-section/imac.png" alt="" srcset="">
          <img src="../assets/img/home/first-section/timeleft.png" alt="" srcset="">
          <img src="../assets/img/home/first-section/money.png" alt="" srcset="">
        </div>
      </div>
    </div>
    <div class="section">
      <div class="wrapper"></div>
      <div class="wrapper">
        <img class="tristan" src="../assets/img/home/tristan-dad.png" alt="">
      </div>
    </div>
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
    .video{
      width: 100%;
      height: 100vh;
      background: $black;
      video {
        width: 100%;
        height: 100%;
      }
    }
    .section {
      height: 100vh;
      width: 100%;
      background: $homeGrey;
      display: flex;
      .wrapper{
        height: 100%;
        width: 50%;
        padding: 0 5%;
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: center;
        .subtitle {
          font-family: Title!important;
          font-size: 7rem;
          margin: 0;
          margin-bottom: 30px;
        }
        .tristan{
          position: absolute;
          height: auto;
          max-height: 80%;
          bottom: 0;
          width: 50%;

        }
        .wrapper--icons{
          display: flex;
          flex-wrap: wrap;
          align-items: center;
          justify-content: space-around;
          margin-top: 30px;
          img {
            margin: 10px;
            width: 40px;
            height: auto;
          }
        }
      }
    }
  }
</style>
