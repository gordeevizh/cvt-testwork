<template>
  <div class="userCardProfileInfo">
    <ul class="userCardProfileInfo__infoTitle">
      <li>Семейное положение</li>
      <li>Телефон</li>
      <li>E-mail</li>
    </ul>
    <ul class="userCardProfileInfo__infoDescription">
      <li>{{maritalStatus}}</li>
      <li>{{phone}}</li>
      <li class="userCardProfileInfo__pseudoLink">{{email}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserCardProfileInfo',
  props: {
    maritalStatus: {
      default: 'Неопределен',
      type: String
    },
    phone: {
      default: 'Отсутствует',
      type: String
    },
    email: {
      default: 'Отсутствует',
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
  .userCardProfileInfo {
    display: flex;
    font-family: "Arial";
    font-size: 12px;
    line-height: 23px;
    color: black;
    margin-top: 20px;
  }
  .userCardProfileInfo__infoTitle {
    font-weight: bold;
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  .userCardProfileInfo__infoDescription {
    list-style-type: none;
    margin: 0;
    padding-left: 32px;
  }
  .userCardProfileInfo__pseudoLink {
    color: #1574af;
    text-decoration: underline;
  }
</style>
