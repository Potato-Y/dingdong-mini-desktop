<template>
  <div id="app">
    <div id="title-bar" style="z-index: 1">
      <div>
        <router-link id="title-text" class="router-link-text" to="/"
          >띵동업무 간단 데스크탑</router-link
        >
      </div>
      <div>
        <router-link class="router-link-text" to="/About" style="float: right"
          >About</router-link
        >
      </div>
    </div>
    <!-- 타이틀과 분리 -->
    <div style="height: 52px"></div>

    <!-- width 고정크기 설정 -->
    <div style="width: 1200px">
      <!-- 콘텐츠 영역 -->
      <div
        id="router-content"
        v-bind:style="{
          width: 1200 - 4 - hiKoreaLookupPageContentWidth + 'px',
        }"
      >
        <router-view />
      </div>
      <div style="float: right" ref="hi_korea_Lookup_page_content">
        <HiKoreaLookupPageContent />
      </div>
    </div>
  </div>
  <div style="float: left">ⓒ 2022. Potato-Y all rights reserved.</div>
</template>

<script>
import HiKoreaLookupPageContent from "./components/layout/HiKoreaLookupPageContent.vue";
export default {
  name: "app",
  data() {
    return {
      hiKoreaLookupPageContentWidth: 0,
    };
  },
  methods: {
    GetiKoreaLookupPageContentWidth() {
      this.hiKoreaLookupPageContentWidth =
        this.$refs.hi_korea_Lookup_page_content.clientWidth;
    },
  },
  mounted() {
    this.GetiKoreaLookupPageContentWidth();
  },
  components: {
    HiKoreaLookupPageContent,
  },
};
</script>

<style>
@import url("./App.css");
</style>
