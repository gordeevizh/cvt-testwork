<template>
  <div class="userCardProfileInterests">
    <h2 class="userCardProfileInterests__infoTitle">Интересы</h2>
    <UserCardProfileInterestsButton
      v-for="interest in interests"
      :key="interest.id"
      :buttonText="interest"/>
  </div>
</template>

<script>
import UserCardProfileInterestsButton from './UserCardProfileInterestsButton'

export default {
  name: 'UserCardProfileInterests',
  components: {
    UserCardProfileInterestsButton
  },
  props: {
    interests: {
      default () {
        return ['Нет интересов']
      },
      type: Array
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCardProfileInterests {
    margin-top: 30px;
  }
  .userCardProfileInterests__infoTitle {
    font-family: "Arial";
    font-size: 12px;
    line-height: 23px;
    color: black;
    font-weight: bold;
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
</style>
