<template>
<div class="calc-button" :class="{ 'calc-button--operator': isOperator }" @click="clicked">
  {{ value }}
</div>
</template>

<script>
export default {
  name: 'CalcButton',
  data: function() {
    return {
      isOperator: this.isOperatorProp
    }
  },
  props: {
    isOperatorProp: {
      default: false,
      type: Boolean
    },
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

.calc-button--operator {
  background-color: orange;
}
</style>
