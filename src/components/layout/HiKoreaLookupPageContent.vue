<template>
  <div id="total-box">
    <iframe
      id="hikorea-web-page"
      frameborder="0"
      src="https://www.hikorea.go.kr/info/mobileCheckExprYmdByPassNoR.pt"
      >page load faild</iframe
    >
    <div id="months-table">
      <!-- 달력표 -->
      <MonthsTable />
    </div>
  </div>
</template>
<script>
import MonthsTable from "./MonthsTable.vue";
export default {
  name: "HiKoreaLookupPageContent",
  components: {
    MonthsTable,
  },
};
</script>

<style>
#total-box {
  float: right;
  /* border: 2px solid black; */
  background-color: rgba(231, 234, 255, 0.404);
  backdrop-filter: blur(2px);
}

/* 하이코리아 웹 페이지 영역 */
#hikorea-web-page {
  width: 480px;
  /* height: 98%; */
  height: 780px;
}

/* 테이블 위치 조정 */
#months-table {
  font-family: "Nanum Gothic" !important; /* 폰트 적용 */
  float: left;
  padding-top: 200px;
}
</style>
