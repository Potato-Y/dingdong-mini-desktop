<template>
  <div class="contents-box">
    <TimeBriefing />
  </div>
  <div class="contents-box">
    <DateCalculator />
  </div>
  <div class="contents-box">
    <TokenMemo />
  </div>
</template>

<script>
import TimeBriefing from "../../components/layout/TimeBriefing.vue";
import DateCalculator from "../../components/layout/DateCalculator.vue";
import TokenMemo from "../../components/layout/TokenMemo.vue";

export default {
  components: {
    TimeBriefing,
    DateCalculator,
    TokenMemo,
  },
};
</script>

<style>
@import url("./Home.css");
</style>
