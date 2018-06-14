<template>
  <button class="userCardProfileButton">Добавить в друзья</button>
</template>

<script>
export default {
  name: 'UserCardProfileButton',
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCardProfileButton {
    background: linear-gradient(0deg, #e65300, #e68100);
    border: none;
    box-shadow: 0px 1px 2px rgba(0,0,0,0.38);
    width: 100%;
    height: 30px;
    margin-top: 6px;
    border-radius: 3px;
    color: white;
    line-height: 23px;
    font-family: "Arial";
    text-shadow: 0px -1px 0px rgba(0,0,0,0.43);
  }
</style>
