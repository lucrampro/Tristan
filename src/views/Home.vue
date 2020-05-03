<template>
  <div class="home">
    <p class="title--background"> {{ this.project[this.i].title }} </p>
    <p class="number">{{ this.project[this.i].number }}</p>
    <p class="date">{{ this.project[this.i].date }}</p>
  </div>
</template>


<script>
import project from '../content';

export default {

  name: 'home',
  data() {
    return {
      project,
      i: 0,
    };
  },
  mounted() {
    this.changeProject();
  },
  methods: {
    next() {
      if (this.i === this.project.length - 1) {
        this.i = 0;
      } else {
        this.i += 1;
      }
    },
    previous() {
      if (this.i === 0) {
        this.i = this.project.length - 1;
      } else {
        this.i -= 1;
      }
    },
    onScroll(e) {
      if (e.deltaY > 0) {
        this.previous();
      } else if (e.deltaY < 0) {
        this.next();
      }
    },
    onKey(e) {
      const key = e.which || e.keyCode;
      switch (key) {
        case 37:
          this.previous();
          break;
        case 38:
          this.next();
          break;
        case 39:
          this.next();
          break;
        case 40:
          this.previous();
          break;
        default:
          console.log('tu peut changez de projet avec les fleche de ton clavier :)');
      }
    },
    changeProject() {
      document.body.addEventListener('wheel', this.onScroll);
      document.body.addEventListener('keydown', this.onKey);
    },
  },
};
</script>

<style lang="scss">
  @import '../css/style';
  .home {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    position: relative;
    align-items: center;
    justify-content: center;
    background-color: $grey;

    .title--background {
      font-family: Title;
      font-size: 25rem;
      margin: 0;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%) rotate(-10deg);
      color: $darkGrey;
      }
    .number {
      font-family: TextBold;
      font-size: 15rem;
      color: $bluePSA;
      margin: 0;
    }
    .date {
      color: $black;
      font-size: 1.3rem;
    }
  }
</style>
