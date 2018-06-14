<template>
  <div class="userCardProfileTitle">
    <h1 class="userCardProfileTitle__userName">{{userName}}</h1>
    <p class="userCardProfileTitle__address">{{address}}</p>
  </div>
</template>

<script>
export default {
  name: 'UserCardProfileTitle',
  props: {
    userName: {
      default: 'Безымянный',
      type: String
    },
    address: {
      default: 'Адрес не указан',
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
  .userCardProfileTitle {
  }
  .userCardProfileTitle__userName {
    color: black;
    font-family: "Arial";
    font-size: 23px;
    font-weight: normal;
    line-height: 21px;
    margin: 0;
  }
  .userCardProfileTitle__address {
    color: #757575;
    font-family: "Arial";
    font-size: 11px;
    line-height: 21px;
    margin: 0;
  }
</style>
