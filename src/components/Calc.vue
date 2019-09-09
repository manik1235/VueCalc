<template>
<div class="calc">
  <table>
    <tr>
      <td>
        <CalcButton value="7"/>
      </td>
      <td>
        <CalcButton value="8"/>
      </td>
      <td>
        <CalcButton value="9"/>
      </td>
      <td>
        <CalcButton value="+"/>
      </td>
    </tr>
    <tr>
      <td>
        <CalcButton value="4"/>
      </td>
      <td>
        <CalcButton value="5"/>
      </td>
      <td>
        <CalcButton value="6"/>
      </td>
      <td>
        <CalcButton value="-"/>
      </td>
    </tr>
    <tr>
      <td>
        <CalcButton value="1"/>
      </td>
      <td>
        <CalcButton value="2"/>
      </td>
      <td>
        <CalcButton value="3"/>
      </td>
      <td>
        <CalcButton value="*"/>
      </td>
    </tr>
    <tr>
      <td>
        <CalcButton value="C"/>
      </td>
      <td>
        <CalcButton value="0"/>
      </td>
      <td>
        <CalcButton value="."/>
      </td>
      <td>
        <CalcButton value="/"/>
      </td>
    </tr>
  </table>
</div>
</template>

<script>
import CalcButton from './CalcButton.vue'

export default {
  name: 'Calc',
  components: {
    CalcButton
  }
}
</script>

<style>
</style>
