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
    isOperator(value) {
      return this.operators.includes(value)
    },
    nextValue(value) {
      var isOperator = !!this.operators.find(function (operator) { return operator === value } )

      if (value === 'C') {
        this.displayValue = '0'
        this.registerValue = 0
        this.registerOperator = '+'
      }

      if (isOperator) {
        if (this.registerOperator === '+') {
          this.displayValue = (this.registerValue + parseFloat(this.displayValue)).toString()
        } else if (this.registerOperator === '-') {
          this.displayValue = (this.registerValue - parseFloat(this.displayValue)).toString()
        } else if (this.registerOperator === '*') {
          this.displayValue = (this.registerValue * parseFloat(this.displayValue)).toString()
        } else if (this.registerOperator === '/') {
          this.displayValue = (this.registerValue / parseFloat(this.displayValue)).toString()
        }
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
