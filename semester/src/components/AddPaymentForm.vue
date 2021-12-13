<template>
  <div :class="$style.paymentForm">
    <button :class="$style.addButton" @click="addPayment">Add +</button>
    <input :class="$style.input" type="text" placeholder="Date" v-model="date">
    <input :class="$style.input" type="text" placeholder="Category" v-model="category">
    <input :class="$style.input" type="text" placeholder="Price" v-model="price">
  </div>
</template>

<script>
export default {
  name: 'AddPaymentForm',
  data() {
    return {
      number: 1,
      date: '',
      category: '',
      price: '',
      show: false,
    };
  },
  computed: {
    paymentDate() {
      const currentDate = new Date();
      const day = currentDate.getDate();
      const month = currentDate.getMonth() + 1;
      const year = currentDate.getFullYear();

      return `${day}.${month}.${year}`;
    },
    // countNumber() {
    //   if (addPayment()) {
    //     this.number++;
    //   }
    // },
  },
  methods: {
    addPayment() {
      const {
        number, date, category, price,
      } = this;
      const data = {
        number: +number,
        date: date || this.paymentDate,
        category,
        price: +price,
      };

      this.$emit('add-payment', data);
    },
  },
};
</script>

<style module>
  .paymentForm {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
  }
  .input {
    margin-top: 10px;
  }
  .addButton {
    margin-top: 10px;
    padding: 5px 30px;
    align-self: flex-start;
    border: 2px solid cadetblue;
    background-color: cadetblue;
    color: aliceblue;
    border-radius: 10px;
  }

</style>
