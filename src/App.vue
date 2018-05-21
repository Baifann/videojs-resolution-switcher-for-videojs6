<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: "App"
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.vjs-resolution-button .vjs-menu-icon:before {
  content: "\f110";
  font-family: VideoJS;
  font-weight: normal;
  font-style: normal;
  font-size: 1.8em;
  line-height: 1.67em;
}

.vjs-resolution-button .vjs-resolution-button-label {
  font-size: 1em;
  line-height: 3em;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  text-align: center;
  box-sizing: inherit;
}

.vjs-resolution-button .vjs-menu .vjs-menu-content {
  width: 4em;
  left: 50%; /* Center the menu, in it's parent */
  margin-left: -2em; /* half of width, to center */
}

.vjs-resolution-button .vjs-menu li {
  text-transform: none;
  font-size: 1em;
}

#app {
  .video-js .vjs-progress-control .vjs-progress-holder {
    margin: 0 20px 0 10px;
  }
}
</style>
