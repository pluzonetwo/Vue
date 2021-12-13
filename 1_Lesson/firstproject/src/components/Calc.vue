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
    <div>
      <Keyboard class="keyboard" @input-value="addValue"></Keyboard>
    </div>
    <div>
      <input type="radio" id="one" v-model="checkedOperand" value="1">
      <label for="one">Первый операнд</label>
      <input type="radio" id="two" v-model="checkedOperand" value="2">
      <label for="two">Второй операнд</label>
    </div>
  </div>
</template>

<script>
import Keyboard from './Keyboard.vue';

export default {
  name: 'Calc.vue',
  components: { Keyboard },
  data: () => ({
    operand1: '',
    operand2: '',
    checkedOperand: '',
    result: 0,
    error: '',
    operators: ['+', '-', '/', '*', '^', '//'],
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
      if (typeof symbol === 'number') {
        if (this.checkedOperand === '1') {
          this.operand1 += `${symbol}`;
        } else {
          this.operand2 += `${symbol}`;
        }
      } else if (this.checkedOperand === '1') {
        this.operand1 = this.operand1.substring(0, this.operand1.length - 1);
      } else {
        this.operand2 = this.operand2.substring(0, this.operand2.length - 1);
      }
    },
  },
};
</script>

<style scoped>

</style>
