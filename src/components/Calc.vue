<template>
<div class="calc">
  <table>
    <tr v-for="row in calculatorArray">
      <td v-for="item in row">
        <CalcButton @buttonClicked="buttonClicked" :value="item"/>
      </td>
    </tr>
  </table>
</div>
</template>

<script>
import CalcButton from './CalcButton.vue'

export default {
  name: 'Calc',
  data() {
    return { calculatorArray: [
      ['7', '8', '9', '+'],
      ['4', '5', '6', '-'],
      ['1', '2', '3', '*'],
      ['C', '0', '.', '/']
    ]}
  },
  components: {
    CalcButton
  },
  methods: {
    buttonClicked(value) {
      console.log(value)
    }
  }
}
</script>

<style>
</style>
