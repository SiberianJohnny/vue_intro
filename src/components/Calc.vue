<template>
  <div class="calc">
    <input type="number" v-model.number="number1" />
    <input type="number" v-model.number="number2" />
    = {{ result }}
    <button @click="sum">+</button>
    <button @click="subtraction">-</button>
    <button @click="multi">*</button>
    <button @click="division">/</button>
    <button @click="pow">Exponentiation</button>
    <button @click="int">Integer Division</button>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    number1: 0,
    number2: 0,
    result: 0,
  }),
  methods: {
    sum() {
      this.result = this.number1 + this.number2;
    },
    subtraction() {
      this.result = this.number1 - this.number2;
    },
    multi() {
      this.result = this.number1 * this.number2;
    },
    division() {
      this.result = this.number1 / this.number2;
    },
    pow() {
      this.result = Math.pow(this.number1, this.number2);
    },
    int() {
      this.result = Math.floor(this.number1 / this.number2);
    },
  },
};
</script>

<style>
</style>