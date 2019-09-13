<template>
<div class="calc">
  <table class="text-center">
    <tr>
      <td colspan=4>
        <Display :displayValue="displayValue" />
      </td>
    </tr>
    <tr v-for="row in calculatorArray">
      <td v-for="item in row">
        <CalcButton @nextValue="nextValue" :value="item"/>
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
      register: []
    }
  },
  components: {
    CalcButton,
    Display
  },
  methods: {
    nextValue(value) {
      console.log("Calc.vue#nextValue => " + value)
      this.displayValue = value
      var isOperator = !!this.operators.find(function (operator) { return operator === value } )
      console.log("isOperator = '" + isOperator + "'")

      if (isOperator) {
        if (value === 'C') {
          this.displayValue = '0'
          this.register = []
        }
      }
    }
  }
}
</script>

<style>
.text-center {
  margin-left: auto;
  margin-right: auto;
  max-width: 300px;
  width: 50%;
}
</style>
