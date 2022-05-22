<template>
  <p>
    *단순 메모*<br />
    (본 메모는 단순히 수동으로 카운터를 올리는 메모 역할입니다.)
  </p>
  <it-number-input
    min="1000"
    max="2000"
    style="width: 35px; text-align: center"
    v-model="token1000"
    readonly
  ></it-number-input>

  <it-number-input
    min="2000"
    max="3000"
    style="width: 35px; text-align: center"
    v-model="token2000"
    readonly
  ></it-number-input>

  <it-number-input
    min="3000"
    max="4000"
    style="width: 35px; text-align: center"
    v-model="token3000"
    readonly
  ></it-number-input>

  <it-number-input
    min="4000"
    max="5000"
    style="width: 35px; text-align: center"
    v-model="token4000"
    readonly
  ></it-number-input>

  <it-number-input
    min="5000"
    max="6000"
    style="width: 35px; text-align: center"
    v-model="token5000"
    readonly
  ></it-number-input>
</template>

<script>
export default {
  data() {
    return {
      token1000: 1000,
      token2000: 2000,
      token3000: 3000,
      token4000: 4000,
      token5000: 5000,
    };
  },
  methods: {},
};
</script>

<style></style>
