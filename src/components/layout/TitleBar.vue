<template>
  <div id="title-bar" style="z-index: 1" ref="title_bar">
    <div>
      <router-link id="title-text" class="router-link-text" to="/"
        >띵동업무 간단 데스크탑</router-link
      >
    </div>
    <div id="title-bar-menu">
      <router-link id="router-about" class="router-link-text" to="/About"
        >About</router-link
      >
    </div>
  </div>

  <div v-bind:style="{ height: titleBarHeight + 'px' }"></div>
</template>

<script>
export default {
  name: "TitleBar",
  data() {
    return {
      titleBarHeight: 0,
    };
  },
  methods: {
    getTitleBarHeight() {
      this.titleBarHeight = this.$refs.title_bar.clientHeight;
    },
  },
  mounted() {
    this.getTitleBarHeight();
  },
};
</script>

<style>
#title-bar {
  position: fixed;
  width: 100%;
  background-color: rgba(255, 255, 255, 0.406);
  border-bottom: 1px solid rgba(232, 232, 232, 0.495);
  backdrop-filter: blur(30px);
}

#title-text {
  font-family: "BMDOHYEON";
  font-size: 35px;
  margin: 10px;
  float: left;
  font-weight: bold;
}

.router-link-text {
  color: rgb(0, 0, 0);
  text-decoration: none;
}

#router-about {
  top: 30px;
}

#title-bar-menu {
  height: 100%;
}
</style>
