<template>
  <div>
    <div>
      <input type="number" v-model.number="operand1">
      <input type="number" v-model.number="operand2">
      = {{result}}
    </div>
    <div class="error" v-if="error">
      {{error}}
    </div>
    <div>
      <button
        v-for="operator of operators"
        @click="calculate(operator)"
        :key="operator"
      >{{ operator }}</button>
    </div>
    <Keyboard @input-value="addValue"></Keyboard>
  </div>
</template>

<script>
import Keyboard from './Keyboard.vue';

export default {
  name: 'Calc.vue',
  components: { Keyboard },
  data: () => ({
    operand1: 0,
    operand2: 0,
    result: 0,
    error: '',
    operators: ['+', '-', '/', '*', '^', '//'],
    numbers: [],
  }),
  methods: {
    sum() {
      this.result = this.operand1 + this.operand2;
    },
    substr() {
      this.result = this.operand1 - this.operand2;
    },
    div() {
      if (this.operand2 === 0) {
        this.error = 'На ноль делить нельзя';
      } else this.result = this.operand1 / this.operand2;
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
    calculate(operation) {
      this.error = '';
      switch (operation) {
        case '+': this.sum(); break;
        case '-': this.substr(); break;
        case '/': this.div(); break;
        case '*': this.multi(); break;
        case '^': this.exp(); break;
        case '//': this.rem(); break;
        default:
          break;
      }
    },
    addValue(symbol) {
      this.numbers.push(symbol);
      this.numbers.forEach((item) => {
        if (typeof item === typeof Number) {
          this.operand1 += item;
        } else {
          this.numbers.splice(this.numbers.length - 1, 1);
        }
      });
    },
  },
};
</script>

<style scoped>

</style>
