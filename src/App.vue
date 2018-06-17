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
    justify-content: center;
    width: 100%;
  }

  @media  (min-width: 488px) {
    #app {
      align-items: center;
      height: 100vh;
    }
  }

  @media  (min-width: 0) and (max-width: 487px) {
    #app {
      align-items: flex-start;
      height: auto;
    }
  }
</style>
