<template>
  <div class="contents-box">
    <TimeBriefing />
  </div>
  <div class="contents-box">
    <DateCalculator />
  </div>
</template>

<script>
import TimeBriefing from "../../components/layout/TimeBriefing.vue";
import DateCalculator from "../../components/layout/DateCalculator.vue";

export default {
  components: {
    TimeBriefing,
    DateCalculator,
  },
};
</script>

<style>
@import url("./Home.css");
</style>
