<template>
  <div :class="$style.blockButton">
    <button :class="$style.button" @click="addNewCost" >ADD NEW COST +</button>
  </div>
</template>

<script>
export default {
  name: 'Button',
  methods: {
    addNewCost() {
      this.$emit('add-cost');
    },
  },
};
</script>

<style module>
  .blockButton{
    display: flex;
    align-self: flex-start;
  }
  .button {
    margin-top: 10px;
    padding: 5px 30px;
    align-self: flex-start;
    border: 2px solid cadetblue;
    background-color: cadetblue;
    color: aliceblue;
    border-radius: 10px;
  }
</style>
