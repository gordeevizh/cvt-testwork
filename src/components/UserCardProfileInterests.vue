<template>
  <div class="userCardProfileInterests">
    <h2 class="userCardProfileInterests__infoTitle">Интересы</h2>
    <div class="userCardProfileInterests__buttons">
      <UserCardProfileInterestsButton
      v-for="(interest, index) in interests"
      :key="interest.id"
      :buttonText="interest"
      @click.native="remove(index)"/>
    </div>
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
        return ['N.E.E.T.']
      },
      type: Array
    }
  },
  methods: {
    remove (interestIndex) {
      this.$emit('removeInterest', interestIndex)
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
  .userCardProfileInterests__buttons {
    display: flex;
    flex-wrap: wrap;
  }
</style>
