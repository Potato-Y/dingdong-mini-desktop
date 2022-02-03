<template>
  <p>
    * 기준 날짜를 입력하세요!
    <input
      type="text"
      v-model="selectedDateUserTextBox"
      oninput="this.value = this.value.replace(/[^0-9]/g, '');"
      style="width: 80px"
      @input="inputSelectDate($event)"
      maxlength="8"
    />
    <button @click="reset">초기화</button><br />
    {{ saveSelectedDate }} 로부터 오늘은 {{ referenceDateDifference }} 일째예요!
    (오늘 미포함)
  </p>
  <br />
  <p>
    <!-- 1 번째 계산기 -->
    D -&nbsp;
    <input
      type="text"
      v-model="cal1"
      @input="inputCal1($event)"
      oninput="this.value = this.value.replace(/[^0-9]/g, '');"
      style="width: 40px"
      maxlength="5"
    />
    은
    <input type="text" style="width: 80px" v-model="calResult1" readonly />
    입니다.
  </p>
  <p>
    <!-- 2 번째 계산기 -->
    D -&nbsp;
    <input
      type="text"
      v-model="cal2"
      oninput="this.value = this.value.replace(/[^0-9]/g, '');"
      style="width: 40px"
      @input="inputCal2($event)"
      maxlength="5"
    />
    은 <input type="text" style="width: 80px" v-model="calResult2" readonly />
    입니다.
  </p>
  <p>
    <!-- 3 번째 계산기 -->
    D +
    <input
      type="text"
      v-model="cal3"
      oninput="this.value = this.value.replace(/[^0-9]/g, '');"
      style="width: 40px"
      @input="inputCal3($event)"
      maxlength="5"
    />
    은 <input type="text" style="width: 80px" v-model="calResult3" readonly />
    입니다. (오늘 미포함)
  </p>
</template>

<script>
export default {
  data() {
    return {
      selectedDateUserTextBox: "00000000", // 유저가 입력한 날짜
      krDate: new Date(), // 한국 날짜 저장
      selectedDate: new Date(),
      referenceDateDifference: 1,
      saveSelectedDate: "",
      cal1: "",
      cal2: "",
      cal3: "",
      calResult1: "",
      calResult2: "",
      calResult3: "",
    };
  },
  methods: {
    reset() {
      // 초기화
      this.resetDate(); // 한국 시간 초기화

      const year = this.krDate.getFullYear();
      const month = ("00" + (this.krDate.getMonth() + 1)).slice(-2);
      const date = ("00" + this.krDate.getDate()).slice(-2);

      this.selectedDateUserTextBox =
        year.toString() + month.toString() + date.toString();

      // 계산기에 기본으로 계산할 날짜 부여
      this.cal1 = 90;
      this.cal2 = 20;
      this.cal3 = 90;

      this.selectedDate = this.krDate; // 선택 날짜 객체에도 한국 날짜 추가

      const tempValue = { target: { value: this.selectedDateUserTextBox } };
      this.inputSelectDate(tempValue);
    },

    resetDate() {
      const localDate = new Date(); // locale 시간

      // UTC 시간 계산
      const utc =
        localDate.getTime() + localDate.getTimezoneOffset() * 60 * 1000;

      // UTC -> KST (UTC + 9 시간)
      const KR_TIME_EIFF = 9 * 60 * 60 * 1000;
      this.krDate = new Date(utc + KR_TIME_EIFF);
    },

    inputSelectDate(event) {
      //입력한 기준날에 맞게 Date객체 생성
      this.resetDate(); // 한국 시간 초기화

      const inputDate = event.target.value;
      if (event.target.value.length == 8) {
        this.selectedDate = new Date(
          Number(inputDate.slice(0, 4)),
          Number(inputDate.slice(4, 6)) - 1,
          Number(inputDate.slice(6, 8))
        );

        var calValue = Math.floor(
          (this.selectedDate.getTime() - this.krDate.getTime()) /
            (1000 * 60 * 60 * 24)
        );

        if (calValue >= -1) {
          calValue += 2;
        } else {
          calValue += 1;
        }

        this.saveSelectedDate = this.calDateToFormat();

        this.referenceDateDifference = calValue;
        this.calRun();
      } else {
        this.dateDifference = 1;
      }
    },

    calDateToFormat() {
      const year = this.selectedDate.getFullYear();
      const month = ("00" + (this.selectedDate.getMonth() + 1)).slice(-2);
      const date = ("00" + this.selectedDate.getDate()).slice(-2);

      return year.toString() + "-" + month.toString() + "-" + date.toString();
    },

    inputCal1(event) {
      const inputValue = event.target.value;

      if (isNaN(inputValue)) return;
      if (inputValue == "") return;
      this.selectedDate.setDate(
        this.selectedDate.getDate() - Number(inputValue)
      );

      // 결괏값 저장하기
      this.calResult1 = this.calDateToFormat();

      // 다시 더해서 selectedDate를 원래대로 돌려두기.
      this.selectedDate.setDate(
        this.selectedDate.getDate() + Number(inputValue)
      );
    },

    inputCal2(event) {
      const inputValue = event.target.value;

      if (isNaN(inputValue)) return;
      if (inputValue == "") return;
      this.selectedDate.setDate(
        this.selectedDate.getDate() - Number(inputValue)
      );

      // 결괏값 저장하기
      this.calResult2 = this.calDateToFormat();

      // 다시 더해서 selectedDate를 원래대로 돌려두기.
      this.selectedDate.setDate(
        this.selectedDate.getDate() + Number(inputValue)
      );
    },

    inputCal3(event) {
      const inputValue = event.target.value;

      if (isNaN(inputValue)) return;
      if (inputValue == "") return;
      this.selectedDate.setDate(
        this.selectedDate.getDate() + Number(inputValue)
      );

      // 결괏값 저장하기
      this.calResult3 = this.calDateToFormat();

      // 다시 더해서 selectedDate를 원래대로 돌려두기.
      this.selectedDate.setDate(
        this.selectedDate.getDate() - Number(inputValue)
      );
    },

    calRun() {
      // 1 번째 페이지 오픈 시 값 적용
      var temCalValue = { target: { value: this.cal1 } };
      this.inputCal1(temCalValue);

      // 2 번째 페이지 오픈 시 값 적용
      temCalValue = { target: { value: this.cal2 } };
      this.inputCal2(temCalValue);

      // 3 번째 페이지 오픈 시 값 적용
      temCalValue = { target: { value: this.cal3 } };
      this.inputCal3(temCalValue);
    },
  },

  mounted() {
    this.resetDate();
    this.reset();
    this.calRun();
  },
};
</script>
