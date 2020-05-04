<template>
  <div id="app">
    <div class="menu">
      <p>tristan</p>
      <div class="link">
        <router-link to='/'>home</router-link>
        <router-link to='/works'>works</router-link>
      </div>
    </div>
    <router-view/>
  </div>
</template>
<style lang="scss">
.menu{
  position: fixed;
  z-index: 9999;
  display: flex;
  height: 150px;
  width: 100vw;
  align-items: center;
  justify-content: space-between;
  mix-blend-mode: difference;
  p {
    font-family: Logo;
    color: white;
    font-size: 80px;
    margin: 0;
    padding-left: 10px;
    transform: rotate(-15deg);
  }
  a {
    font-family: TextBold;
    outline: none;
    text-decoration: none;
    color: white;
    margin: 0px 10px;
  }
}
</style>
