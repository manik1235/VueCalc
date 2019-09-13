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
      console.log("CalcButton.vue#clicked.value == " + this.value)
      this.$emit("nextValue", this.value)
    }
  }
}
</script>

<style>
</style>
