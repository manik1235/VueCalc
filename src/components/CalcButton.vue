<template>
<button class="calc-button" :class="{ 'calc-button--operator': isOperator, 'calc-button--depressed': isDepressed }" @click="clicked">
  {{ value }}
</button>
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
    isDepressed: {
      default: false,
      type: Boolean
    },
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
  font-size: 1em;
  margin: 1px;
  min-height: 20px;
  min-width: 20px;
  padding: 2px;
}

.calc-button--operator {
  background-color: orange;
}

.calc-button--depressed {
  box-shadow: inset 0px 0px 5px #4d2600;
}
</style>
