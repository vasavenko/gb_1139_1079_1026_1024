<template>
  <div class="calc">
    {{ message }}
    {{ message.length }}
    {{ message.split().reverse().join() }}

    <div>
      <input
        type="number"
        placeholder="Operand1"
        v-on:focus="onFocus"
        v-model.number="operand1"
      />
      <input
        type="number"
        placeholder="Operand2"
        @keyup="onKeyUp"
        v-model.number="operand2"
      />
      = {{ result }}
      <div class="keyboard">
        <button @click="result = operand1 + operand2">+</button>
        <button @click="div">-</button>
        <button v-on:click="multi(operand1, operand2)">*</button>
        <button @click="result = operand1 / operand2">/</button>
        <button @click="exp">**</button>
        <button @click="intDiv">%</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    message: "Hello Vue",
    operand1: 0,
    operand2: 0,
    result: 0,
    array: [],
  }),
  methods: {
    doThan(text, event) {
      console.log(text, event);
    },
    div() {
      this.result = this.operand1 - this.operand2;
    },
    multi(op1, op2) {
      this.result = op1 * op2;
    },
    exp() {
      this.result = this.operand1 ** this.operand2;
    },
    intDiv() {
      this.result = Math.floor(this.operand1 / this.operand2);
    },
    onFocus() {
      console.log("onFocus");
    },
    onKeyUp() {
      console.log("onKeyUp");
    },
  },
};
</script>
