<template>
  <div>
    <div>
      <h1>КАЛЬКУЛЯТОР</h1>
    </div>
    <div>
      <input type="number" placeholder="op1" v-model.number="operand1" />
      <input type="number" placeholder="op2" v-model.number="operand2" />
      = {{ sum }}
    </div>
    <div>
      <button @click="sum = operand1 + operand2">+</button>
      <button @click="sum = operand1 - operand2">-</button>
      <button @click="sum = operand1 * operand2">*</button>
      <button @click="div">/</button>
      <button @click="eventFv">Event</button>
    </div>
    <div>
      <button @click="pow">n&#739;</button>
      <button @click="trunc">&#247;</button>
    </div>
    result : {{ sum }}
    <div>
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox"></label>
      <span>Отобразить экранную клавиатуру</span>
      <template v-if="checked == true">
        <div>
          <button
            v-for="item in numbers"
            v-bind:key="item"
            v-bind:title="item"
            @click="clickOp1(item)"
          >
            {{ item }}
          </button>
          <button @click="del">&#8592;</button>
        </div>
      </template>
    </div>

    <div>
      <input type="radio" id="one" value="Один" v-model="picked" />
      <label for="one">Операнд 1</label>
      <input type="radio" id="two" value="Два" v-model="picked" />
      <label for="two">Операнд 2</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calc",
  data: () => ({
    operand1: 0,
    operand2: 0,
    sum: 0,
    numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    checked: true,
    picked: "",
  }),
  methods: {
    eventFv() {
      console.log(arguments);
    },
    div() {
      if (this.operand2 === 0) {
        this.sum = "Cannot divide by zero";
      } else {
        this.sum = this.operand1 / this.operand2;
      }
    },
    pow() {
      this.sum = Math.pow(this.operand1, this.operand2);
    },
    trunc() {
      if (this.operand2 === 0) {
        this.sum = "Cannot divide by zero";
      } else {
        this.sum = Math.trunc(this.operand1 / this.operand2);
      }
    },
    clickOp1(item) {
      if (this.picked == "Один") {
        this.operand1 = Number(`${this.operand1}${item}`);
      } else {
        this.operand2 = Number(`${this.operand2}${item}`);
      }
    },
    del() {
      if (this.picked == "Один") {
        this.operand1 = Number(
          String(this.operand1).slice(0, String(this.operand1).length - 1)
        );
      } else {
        this.operand2 = Number(
          String(this.operand2).slice(0, String(this.operand2).length - 1)
        );
      }
    },
  },
};
</script>