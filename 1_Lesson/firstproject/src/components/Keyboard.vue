<template>
 <div>
   <div>
     <input class="checkbox" type="checkbox" id="keyboard" v-model="checked">
     <label for="keyboard">Показать клавиатуру</label>
   </div>
   <div v-if="checked">
     <button
       v-for="symbol of keyboardSymbols"
       @click="add(symbol)"
       :key="symbol"
     >{{symbol}}</button>
   </div>
 </div>
</template>

<script>
export default {
  name: 'Keyboard.vue',
  data: () => ({
    input: '',
    checked: false,
    keyboardSymbols: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, '🠐'],
  }),
  methods: {
    add(symbol) {
      this.$emit('input-value', symbol);
    },
  },
};
</script>

<style scoped>

</style>
