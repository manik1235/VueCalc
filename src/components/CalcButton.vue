<template>
<div class="calc-button" @click="clicked">
  {{ value }}
</div>
</template>

<script>
export default {
  name: 'CalcButton',
  props: {
    value: String
  },
  methods: {
    clicked() {
      this.$emit("nextValue", this.value)
    }
  }
}
</script>

<style>
.calc-button {
  border: 1px solid grey;
  border-radius: 3px;
  margin: 1px;
  padding: 2px;
}
</style>
