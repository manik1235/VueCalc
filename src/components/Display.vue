<template>
<div class="display">
  <div class="display-module text-right">
    {{ displayValue }}
  </div>
</div>
</template>

<script>
export default {
  name: 'Display',
  props: {
    displayValue: String
  }
}
</script>

<style>
.display-module {
  border: 2px solid black;
  font-family: monaco, Consolas, Lucida Console, monospace;
  padding-left: 3px;
  padding-right: 3px;
}

.text-right {
  text-align: right;
}
</style>
