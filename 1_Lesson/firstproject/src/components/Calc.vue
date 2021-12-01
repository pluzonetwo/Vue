<template>
  <div>
    <div>
      <input type="number" v-model="operand1">
      <input type="number" v-model="operand2">
      = {{result}}
    </div>
    <div>
      <button @click="sum">+</button>
      <button @click="substr">-</button>
      <button @click="div">/</button>
      <button @click="multi">*</button>
      <button @click="exp">^</button>
      <button @click="rem">//</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calc.vue',
  data: () => ({
    operand1: 0,
    operand2: 0,
    result: 0,
  }),
  methods: {
    sum() {
      this.result = +this.operand1 + +this.operand2;
    },
    substr() {
      this.result = this.operand1 - this.operand2;
    },
    div() {
      this.result = this.operand1 / this.operand2;
    },
    multi() {
      this.result = this.operand1 * this.operand2;
    },
    exp() {
      this.result = this.operand1 ** this.operand2;
    },
    rem() {
      this.result = Math.floor(this.operand1 / this.operand2);
    },
  },
};
</script>

<style scoped>

</style>
