<template>
  <div class="calc">
    <input type="number" v-model.number="number1" />
    <input type="number" v-model.number="number2" />
    <br />
    = {{ result }}
    <br />

    <div class="error" v-if="!!error">Ошибка: {{ error }}</div>

    <button
      v-for="item in operations"
      :key="item"
      @click="calculate(item)"
      :title="item"
    >
      {{ item }}
    </button>

    <div class="logs">
      Logs:
      <br />
      <div v-for="(log, id) in logs" :key="id">{{ log }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    number1: 0,
    number2: 0,
    result: 0,
    error: "",
    operations: ["+", "-", "*", "/", "Exponentiation", "Integer Division"],
    logs: {},
  }),
  methods: {
    calculate(operation) {
      this.error = "";
      switch (operation) {
        case "+":
          this.sum();
          break;
        case "-":
          this.subtraction();
          break;
        case "*":
          this.multi();
          break;
        case "/":
          this.division();
          break;
        case "Exponentiation":
          this.pow();
          break;
        case "Integer Division":
          this.int();
          break;
      }
      const key = Date.now();
      const value = `${this.number1} ${operation} ${this.number2} = ${this.result}`;
      this.$set(this.logs, key, value);
    },
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
      if (this.number1 === 0 || this.number2 === 0) {
        this.error = "Я вам запрещаю делить на 0.";
      } else {
        this.result = this.number1 / this.number2;
      }
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