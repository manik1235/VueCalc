<template>
<div @click="clicked" class="CalcButton">
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
      this.$emit("buttonClicked", this.value)
    }
  }
}
</script>

<style>
</style>
