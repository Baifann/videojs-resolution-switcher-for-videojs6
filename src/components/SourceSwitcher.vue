<template>
  <div :style="width?`width: ${width}`: ''">
    <div class="switch-current-play-title">4M</div>
    <div class="switch-menu-layout">
      <div>8M</div>
      <div>9M</div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},

  props: {
    width: {
      type: String,
      default: null
    }
  },

  data() {
    return {};
  },

  mounted() {},

  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.switch-current-play-title {
  position: relative;
}

.switch-menu-layout {
  position: absolute;
  bottom: 0px;
  left: 0px;
}
</style>
