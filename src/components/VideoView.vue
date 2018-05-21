<template>
  <div class="container">
    <div class="player">
      <video-player  class="video-player vjs-custom-skin"
        ref="videoPlayer"
        :playsinline="true"
        :options="playOptions"
        @play="onPlayerPlay($event)"
        @pause="onPlayerPause($event)"
        @timeupdate="onPlayerTimeupdate($event)"
        @ready="playerReadied"
      >
      </video-player>
      <source-switcher/>
    </div>
  </div>
</template>

<script>
import { videoPlayer } from "vue-video-player";
import SourceSwitcher from "@/components/SourceSwitcher";

export default {
  components: {
    videoPlayer,
    SourceSwitcher
  },

  props: {
    playOptions: {
      type: Object,
      default: () => {
        return {};
      }
    }
  },

  data() {
    return {};
  },

  created() {},

  methods: {
    onPlayerPlay(player) {
      console.log("play");
      this.$emit("onPlayerPlay", player);
    },
    onPlayerPause(player) {
      console.log("pause");
      this.$emit("onPlayerPause", player);
    },
    onPlayerTimeupdate(player) {
      console.log("player Timeupdate!", player.currentTime());
      this.$emit("timeupdate", player);
    },
    playerReadied(player) {
      this.$emit("ready", player);
    }
  },

  watch: {},

  computed: {
    player() {
      return this.$refs.videoPlayer.player;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  background-color: #efefef;
  min-height: 100%;
}

</style>
