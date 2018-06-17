<template>
  <BaseButton class="userCardProfileButton">Добавить в друзья</BaseButton>
</template>

<script>
import BaseButton from './BaseButton'
export default {
  name: 'UserCardProfileButton',
  components: {
    BaseButton
  }
}
</script>

<style scoped>
  .userCardProfileButton {
    margin-top: 6px;
  }
</style>
