<template>
  <main id="app">
    <Button @add-cost="show = !show"/>
    <AddPaymentForm v-if="show" @add-payment="addNewPayment"/>
    <ListOfExpenses :items="paymentsList"/>
  </main>
</template>

<script>
import ListOfExpenses from './components/ListOfExpenses.vue';
import AddPaymentForm from './components/AddPaymentForm.vue';
import Button from './components/Button.vue';

export default {
  name: 'App',
  components: {
    ListOfExpenses,
    AddPaymentForm,
    Button,
  },
  data() {
    return {
      paymentsList: [],
      show: false,
    };
  },
  methods: {
    fetchData() {
      return [
        {
          number: 1,
          date: '01.01.2022',
          category: 'Food',
          price: 20,
        },
        {
          number: 2,
          date: '05.01.2022',
          category: 'Chill',
          price: 100,
        },
        {
          number: 3,
          date: '08.01.2022',
          category: 'Presents',
          price: 80,
        },
      ];
    },
    addNewPayment(payment) {
      console.log('addNewPayment', payment);
      this.paymentsList.push(payment);
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
