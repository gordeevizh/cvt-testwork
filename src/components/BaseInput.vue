<template>
  <input
    type="text"
    class="baseInput"
    :value="value"
    @input="$emit('input', $event.target.value)"
    @focus="$emit('focus', $event.target.value)"
    @blur="$emit('blur', $event.target.value)"
  />
</template>

<script>
export default {
  name: 'BaseInput',
  props: {
    value: {
      default: '',
      type: String
    }
  }
}
</script>

<style scoped>
  .baseInput {
    width: 100%;
    height: 30px;
    border: 1px solid #e66b00;
    border-radius: 3px;
    color: black;
    line-height: 23px;
    font-family: "Arial";
    outline: none;
    padding: 0 1em;
    box-sizing: border-box;
  }
</style>
