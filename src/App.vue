<template>
  <div id="app">
    <div id="page-title">띵동업무 간단 데스크탑</div>

    <div id="hikorea-container">
      <iframe
        id="hikorea-web-page"
        frameborder="0"
        src="https://www.hikorea.go.kr/info/mobileCheckExprYmdByPassNoR.pt"
        >page load faild</iframe
      >
      <div id="months-table">
        <table border="1">
          <tr>
            <td>JAN</td>
            <td>1월</td>
          </tr>
          <tr>
            <td>FEB</td>
            <td>2월</td>
          </tr>
          <tr>
            <td>MAR</td>
            <td>3월</td>
          </tr>
          <tr>
            <td>APR</td>
            <td>4월</td>
          </tr>
          <tr>
            <td>MAY</td>
            <td>5월</td>
          </tr>

          <tr>
            <td>JUN</td>
            <td>6월</td>
          </tr>

          <tr>
            <td>JUL</td>
            <td>7월</td>
          </tr>
          <tr>
            <td>AUG</td>
            <td>8월</td>
          </tr>
          <tr>
            <td>SEP</td>
            <td>9월</td>
          </tr>
          <tr>
            <td>OCT</td>
            <td>10월</td>
          </tr>
          <tr>
            <td>NOV</td>
            <td>11월</td>
          </tr>
          <tr>
            <td>DEC</td>
            <td>12월</td>
          </tr>
        </table>
      </div>
    </div>
    <!-- <router-view /> -->
    <br />
    <a href="https://github.com/Potato-Y/dingdong-mini-desktop"
      >사용된 오픈소스 확인하기</a
    >
  </div>
</template>

<style>
/* 배달의 민족 도현체 */
@font-face {
  font-family: "BMDOHYEON";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_one@1.0/BMDOHYEON.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}
/* 나눔고딕 */
@import url(//fonts.googleapis.com/earlyaccess/nanumgothic.css);

.nanumgothic * {
  font-family: "Nanum Gothic", sans-serif;
}

/* 페이지 전체에 적용할 내용 */
#app {
  position: absolute;
  left: 0px;
  top: 0px;
}

/* 타이틀 부분 */
#page-title {
  font-family: "BMDOHYEON" !important; /* 폰트 적용 */
  font-size: 30px;
  text-align: center;
  margin: 5px;
}

/* 하이코리아 관련 영역 */
#hikorea-container {
  border: 3px solid black; /* 테두리 설정 */
  border-radius: 20px;
  margin-left: 5px;
  padding: 5px;
  width: 590px;
}

/* 하이코리아 웹 페이지 영역 */
#hikorea-web-page {
  width: 500px;
  height: 800px;
}

/* 테이블 위치 조정 */
#months-table {
  font-family: "Nanum Gothic" !important; /* 폰트 적용 */
  float: right;
  padding-top: 200px;
}
</style>
