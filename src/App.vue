<template>
  <div id="app">
    <TitleBar />

    <!-- width 고정크기 설정 -->
    <div style="width: 1200px">
      <!-- 콘텐츠 영역 -->
      <div id="router-content">
        <router-view />
        <div id="copy-rights">ⓒ 2022. Potato-Y all rights reserved.</div>
      </div>

      <div style="float: left" ref="hi_korea_Lookup_page_content">
        <HiKoreaLookupPageContent />
      </div>
    </div>
  </div>
</template>

<script>
import TitleBar from "./components/layout/TitleBar.vue";
import HiKoreaLookupPageContent from "./components/layout/HiKoreaLookupPageContent.vue";
export default {
  name: "app",
  components: {
    TitleBar,
    HiKoreaLookupPageContent,
  },
};
</script>

<style>
@import url("./App.css");
</style>
