<template>
  <div class="hello">
     <video id='video' class="video-js vjs-default-skin"></video>
  </div>
</template>

<script>
/* eslint-disable */

import videoJsResolutionSwitcher from "@/util/videojs-resolution-switcher.js";
import videojs from "video.js";
// import videoJsResolutionSwitcher from "@/js/videojs-resolution-switcher.js";
// import videojs from "@/util/video.min.js";

export default {
  components: {
  },

  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      playerOptions: {
        height: "560",
        autoplay: true,
        muted: true,
        language: "en",
        playbackRates: [0.7, 1.0, 1.5, 2.0],
        sources: [
          {
            type: "video/mp4",
            // mp4
            src: "http://vjs.zencdn.net/v/oceans.mp4"
            // webm
            // src: "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
          }
        ],
        poster:
          "https://surmon-china.github.io/vue-quill-editor/static/images/surmon-1.jpg"
      }
    };
  },

  mounted() {
    this.initPlugins();
  },

  methods: {
    initPlugins() {
      videojs(
        "video",
        {
          controls: true,
          plugins: {
            videoJsResolutionSwitcher: {
              default: "low", // Default resolution [{Number}, 'low', 'high'],
              dynamicLabel: true
            }
          }
        },
        function() {
          console.log(this);
          var player = this;
          window.player = player;
          player.updateSrc([
            {
              src: "https://vjs.zencdn.net/v/oceans.mp4?SD",
              type: "video/mp4",
              label: "SD",
              res: 360
            },
            {
              src: "https://vjs.zencdn.net/v/oceans.mp4?HD",
              type: "video/mp4",
              label: "HD",
              res: 720
            }
          ]);
          player.on("resolutionchange", function() {
            console.info("Source changed to %s", player.src());
          });
        }
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
