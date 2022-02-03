<template>
  <p>
    *단순 메모*<br />
    (본 메모는 단순히 수동으로 카운터를 올리는 메모 역할입니다.)
  </p>
  <br />
  1000 :
  <input
    type="text"
    class="token-value"
    v-model="token1000"
    oninput="this.value = this.value.replace(/[^0-9]/g, '');"
    maxlength="4"
    readonly
  />
  <button class="add-minus-button" @click="token1000--">-</button>
  <button class="add-minus-button" @click="token1000++">+</button>

  <br />
  2000 :
  <input
    type="text"
    class="token-value"
    v-model="token2000"
    oninput="this.value = this.value.replace(/[^0-9]/g, '');"
    maxlength="4"
    readonly
  />
  <button class="add-minus-button" @click="token2000--">-</button>
  <button class="add-minus-button" @click="token2000++">+</button>

  <br />
  3000 :
  <input
    type="text"
    class="token-value"
    v-model="token3000"
    oninput="this.value = this.value.replace(/[^0-9]/g, '');"
    maxlength="4"
    readonly
  />
  <button class="add-minus-button" @click="token3000--">-</button>
  <button class="add-minus-button" @click="token3000++">+</button>

  <br />
  4000 :
  <input
    type="text"
    class="token-value"
    v-model="token4000"
    oninput="this.value = this.value.replace(/[^0-9]/g, '');"
    maxlength="4"
    readonly
  />
  <button class="add-minus-button" @click="token4000--">-</button>
  <button class="add-minus-button" @click="token4000++">+</button>

  <br />
  5000 :
  <input
    type="text"
    class="token-value"
    v-model="token5000"
    oninput="this.value = this.value.replace(/[^0-9]/g, '');"
    maxlength="4"
    readonly
  />
  <button class="add-minus-button" @click="token5000--">-</button>
  <button class="add-minus-button" @click="token5000++">+</button>
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

<style>
.add-minus-button {
  margin-left: 5px;
  width: 30px;
}

.token-value {
  width: 40px;
  text-align: center;
}
</style>
