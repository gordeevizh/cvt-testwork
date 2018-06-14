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
  },
  data () {
    return {
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
    line-height: 23px;
    font-size: 12px;
    font-family: "Arial";
  }
</style>
