<template>
    <div>
        <div>
            <h1>КАЛЬКУЛЯТОР</h1>
        </div>
        <div>
            <input type="number" placeholder="op1" v-model.number="operand1">
            <input type="number" placeholder="op2" v-model.number="operand2"/>
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
    </div>
</template>

<script>
export default {
    name: "Calc",
    data: () => ({
        operand1: 0,
        operand2: 0,
        sum: 0
    }),
    methods: {
        eventFv(){
            console.log(arguments)
        },
        div(){
            if (this.operand2 === 0) {
                this.sum = 'Cannot divide by zero'
            } else {
                this.sum = this.operand1 / this.operand2
            }
        },
        pow(){
            this.sum = Math.pow(this.operand1, this.operand2)
        },
        trunc(){
            if (this.operand2 === 0) {
                this.sum = 'Cannot divide by zero'
            } else {
                this.sum = Math.trunc(this.operand1 / this.operand2)
            }
        }
    },
}
</script>