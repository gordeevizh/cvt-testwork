<template>
  <div class="userCard">
    <UserCardNavigation/>
    <UserCardProfile/>
  </div>
</template>

<script>
import UserCardNavigation from './UserCardNavigation'
import UserCardProfile from './UserCardProfile'

export default {
  name: 'UserCard',
  components: {
    UserCardNavigation,
    UserCardProfile
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCard {
  }
</style>
