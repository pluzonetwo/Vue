<template>
  <main>
    <div>
      <table :class="$style.table">
        <tr :class="$style.tr">
          <th>№</th>
          <th>Date</th>
          <th>Category</th>
          <th>Price</th>
        </tr>
        <tr :class="$style.tr" v-for="(item, index) in items" :key="index">
          <td>{{index + 1}}</td>
          <td>{{item.date}}</td>
          <td>{{item.category}}</td>
          <td>{{item.price}}</td>
        </tr>
      </table>
    </div>
  </main>
</template>

<script>
export default {
  name: 'ListOfExpenses.vue',
  props: {
    items: {
      type: Array,
      required: true,
    },
    msg: String,
  },
};
</script>

<style module>
  .table {
    width: 30%;
    margin-top: 30px;
  }
  .tr {

  }
</style>
