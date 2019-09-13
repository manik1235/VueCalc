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
    return { calculatorArray: [
      ['7', '8', '9', '+'],
      ['4', '5', '6', '-'],
      ['1', '2', '3', '*'],
      ['C', '0', '.', '/']
    ], displayValue: '0' }
  },
  components: {
    CalcButton,
    Display
  },
  methods: {
    nextValue(value) {
      console.log("Calc.vue#nextValue => " + value)
      this.displayValue = value
    }
  }
}
</script>

<style>
.text-center {
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
</style>
