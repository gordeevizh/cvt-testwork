<template>
  <button class="userCardProfileInterestsButton">{{buttonText}}</button>
</template>

<script>
export default {
  name: 'UserCardProfileInterestsButton',
  props: {
    buttonText: {
      default: '',
      type: String
    }
  }
}
</script>

<style scoped>
  .userCardProfileInterestsButton {
    background: white;
    border: 1px solid #d5d5d5;
    height: 25px;
    border-radius: 3px;
    color: #1574af;
    cursor: pointer;
    line-height: 23px;
    font-size: 12px;
    font-family: "Arial";
    margin: 0 3px 3px 0;
    outline: none;
  }
  .userCardProfileInterestsButton:hover {
    background: #f3f3f3;
    border: 1px solid #d5d5d5;
    color: black;
  }
</style>
