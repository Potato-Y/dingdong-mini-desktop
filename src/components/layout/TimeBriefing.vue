<template>
  <div>
    <p class="now-time-basic">
      현재 시간&nbsp; {{ nowTimeYear }}-{{ nowTimeMonth }}-{{ nowTimeDate }} ({{
        nowTimeDay
      }})&nbsp;&nbsp;{{ nowTimeHur }}:{{ nowTimeMin }}
      <span id="now-time-sec">:&nbsp;&nbsp;{{ nowTimeSec }}</span>
    </p>
    11:30 오전 번호표 마감<br />
    17:30 오후 번호표 마감
  </div>
</template>

<script>
export default {
  name: "TimeBriefing",
  data() {
    return {
      nowTimeYear: "0000",
      nowTimeMonth: "00",
      nowTimeDate: "00",
      nowTimeDay: "",
      nowTimeHur: "00",
      nowTimeMin: "00",
      nowTimeSec: "00",
    };
  },
  methods: {
    timeUpdate() {
      // 컴퓨터의 표준 시간 상관 없이 항상 한국 시간이 나타나도록 하기
      const localDate = new Date(); // locale 시간

      // UTC 시간 계산
      const utc =
        localDate.getTime() + localDate.getTimezoneOffset() * 60 * 1000;

      // UTC -> KST (UTC + 9 시간)
      const KR_TIME_EIFF = 9 * 60 * 60 * 1000;
      const krDate = new Date(utc + KR_TIME_EIFF);

      this.nowTimeYear = krDate.getFullYear();
      this.nowTimeMonth = ("00" + (krDate.getMonth() + 1)).slice(-2);
      this.nowTimeDate = krDate.getDate();
      this.nowTimeDay = this.getDay(krDate.getDay());

      this.nowTimeHur = ("00" + krDate.getHours()).slice(-2);
      this.nowTimeMin = ("00" + krDate.getMinutes()).slice(-2);
      this.nowTimeSec = ("00" + krDate.getSeconds()).slice(-2);

      setTimeout(this.timeUpdate, 1000);
    },
    getDay(day) {
      switch (day) {
        case 0:
          return "일";
        case 1:
          return "월";
        case 2:
          return "화";
        case 3:
          return "수";
        case 4:
          return "목";
        case 5:
          return "금";
        case 6:
          return "토";
      }
    },
  },
  mounted() {
    this.timeUpdate();
  },
};
</script>

<style>
.now-time-basic {
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 15px;
}

#now-time-sec {
  font-size: 20px;
}
</style>
