<template>
<div class="calculator">
  <table class="display-pad">
    <tr>
      <td colspan=4>
        <Display :displayValue="displayValue" />
      </td>
    </tr>
    <tr v-for="row in calculatorArray" :key="row.id">
      <td v-for="item in row" :key="item.id">
        <CalcButton
          @nextValue="nextValue"
          :value="item"
          :isDepressed="isDepressed(item)"
          :isOperatorProp="isOperator(item)"/>
      </td>
    </tr>
  </table>
</div>
</template>

<script>
import CalcButton from './CalcButton.vue'
import Display from './Display.vue'

export default {
  name: 'Calc',
  data() {
    return { calculatorArray:
      [['7', '8', '9', '+'],
       ['4', '5', '6', '-'],
       ['1', '2', '3', '*'],
       ['C', '0', '.', '/']],
      displayValue: '0',
      lastValue: '',
      operators: ['+', '-', '*', '/', 'C'],
      register: '',
      registerOperator: '+',
      registerValue: 0,
      newValue: true
    }
  },
  components: {
    CalcButton,
    Display
  },
  methods: {
    isDepressed(item) {
      return this.registerOperator === item
    },
    isOperator(item) {
      return this.operators.includes(item)
    },
    calculate(registerOperator, registerValue, displayValue) {
      displayValue = parseFloat(displayValue)
      if (registerOperator === '+') {
        displayValue = registerValue + displayValue
      } else if (registerOperator === '-') {
        displayValue = registerValue - displayValue
      } else if (registerOperator === '*') {
        displayValue = registerValue * displayValue
      } else if (registerOperator === '/') {
        displayValue = registerValue / displayValue
      }
      return displayValue.toString()
    },
    nextValue(value) {
      if (value === 'C') {
        this.displayValue = '0'
        this.registerValue = 0
        this.registerOperator = '+'
        this.lastValue = ''
      }

      if (this.isOperator(value)) {
        this.displayValue = this.calculate(this.registerOperator, this.registerValue, this.displayValue)
        this.registerValue = parseFloat(this.displayValue)
        this.registerOperator = value
        this.newValue = true
      } else {
        if (this.newValue) {
          // Clear the display if an operator was just pressed prior to this value
          this.newValue = false
          this.displayValue = value
        } else {
          // Numbers are pushed directly into the register & display
          this.displayValue += value
        }
      }
    }
  }
}
</script>

<style>
.calculator {
  border: 3px solid silver;
  border-radius: 15px;
  margin-left: auto;
  margin-right: auto;
  max-width: 300px;
  padding: 30px 30px;
  width: 50%;
}

.display-pad {
  margin-left: auto;
  margin-right: auto;
  max-width: 300px;
  width: 50%;
}
</style>
