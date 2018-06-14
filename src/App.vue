<template>
  <div id="app">
    <UserCard/>
  </div>
</template>

<script>
import UserCard from './components/UserCard.vue'

export default {
  name: 'App',
  components: {
    UserCard
  }
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;
  }

  #app {
    background: url('/static/img/Background.png');
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 100%;
  }
</style>
