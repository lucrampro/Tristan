<template>
  <div class="works">
    <p class="title--background"> {{ this.project[this.i].title }} </p>
    <p class="number" :style='numberColor'>{{ this.project[this.i].number }}</p>
    <p class="number second" :style='shadowColor'>{{ this.project[this.i].number }}</p>
    <div class="logo"> <img :src="this.project[i].logo" alt="" srcset=""> </div>
    <p class="date">{{ this.project[this.i].date }}</p>
  </div>
</template>


<script>
// IMPORT of modules
import gsap from 'gsap';
// IMPORT of components
import project from '../content';

export default {

  name: 'Works',
  mounted() {
    this.changeProject();

    // this.nextTl.to('.second', 0.5, { top: '50%', left: '50%' }, 'start')
    //   .to('.logo', 0.5, { rotate: '90deg', opacity: 0 }, 'start')
    //   .to('.title--background, .date', 0.5, { opacity: 0 }, 'start')
    //   .to('.number', 0.5, { scale: 0, onComplete: () => { this.i += 1; } })
    //   .to('.number', 0.5, { scale: 1 })
    //   .to('.second', 0.5, { top: '51%', left: '51%' }, 'sndStep')
    //   .to('.title--background, .date', 0.5, { opacity: 1 }, 'sndStep')
    //   .to('.logo', 0.5, { rotate: '0deg', opacity: 1 });
  },
  data() {
    return {
      project,
      i: 0,
      nextTl: gsap.timeline({ paused: true }),
    };
  },
  methods: {
    next() {
      if (this.i === this.project.length - 1) {
        this.animationProjectChange();
        // this.i = 0
      } else {
        this.animationProjectChange();
        // this.i += 1
      }
    },
    previous() {
      if (this.i === 0) {
        this.animationProjectChange();
        // this.i = this.project.length - 1
      } else {
        this.animationProjectChange();
        // this.i -= 1
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
    animationProjectChange(e) {
      this.nextTl.to('.second', 0.5, { top: '50%', left: '50%' }, 'start')
        .to('.logo', 0.5, { rotate: '90deg', opacity: 0 }, 'start')
        .to('.title--background, .date', 0.5, { opacity: 0 }, 'start')
        .to('.number', 0.5, { scale: 0, onComplete: () => e })
        .to('.number', 0.5, { scale: 1 })
        .to('.second', 0.5, { top: '51%', left: '51%' }, 'sndStep')
        .to('.title--background, .date', 0.5, { opacity: 1 }, 'sndStep')
        .to('.logo', 0.5, { rotate: '0deg', opacity: 1 })
        .play();
    },
  },
  computed: {
    numberColor() {
      return {
        color: `${this.project[this.i].color}`,
      };
    },
    shadowColor() {
      return {
        color: `${this.project[this.i].shadow}`,
      };
    },
  },
};
</script>

<style lang="scss">
  @import '../css/style';
  .works {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    position: relative;
    background-color: $grey;
    .title--background {
      cursor: default;
      font-family: Title;
      font-size: 20rem;
      margin: 0;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%) rotate(-10deg);
      color: $darkGrey;
      }
    .number {
      cursor: pointer;
      font-family: TextBold;
      font-size: 20rem;
      margin: 0;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: 3;
      &.second {
        top: 51%;
        left: 51%;
        z-index: 1;
      }
    }
    .logo {
      height: 12vh;
      width: 17vw;
      position: absolute;
      top: 35%;
      left: 55%;
      background: #fefefe;
      z-index: 2;
      display: flex;
      justify-content: center;
      align-items: center;
      transform-origin: top left;
      img {
        display: block;
        max-width: 100%;
        max-height: 100%;
      }
    }
    .date {
      color: $black;
      font-size: 1.3rem;
      position: absolute;
      top: 70%;
      left: 50%;
      transform: translate(-50%,-50%);
    }
  }
</style>
