<template>
  <div class="userCardProfile">
    <div class="userCardProfile__colLeft">
      <UserCardProfileImage/>
      <UserCardProfileButton/>
    </div>
    <div class="userCardProfile__colRight">
      <UserCardProfileTitle/>
      <UserCardProfileInfo/>
      <UserCardProfileInterests/>
    </div>
  </div>
</template>

<script>
import UserCardProfileImage from './UserCardProfileImage'
import UserCardProfileButton from './UserCardProfileButton'
import UserCardProfileTitle from './UserCardProfileTitle'
import UserCardProfileInfo from './UserCardProfileInfo'
import UserCardProfileInterests from './UserCardProfileInterests'

export default {
  name: 'UserCardProfile',
  components: {
    UserCardProfileImage,
    UserCardProfileButton,
    UserCardProfileTitle,
    UserCardProfileInfo,
    UserCardProfileInterests
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCardProfile {
    display: flex;
  }
  .userCardProfile__colLeft {
    margin: 15px;
  }
  .userCardProfile__colRight {
    margin: 15px 15px 15px 5px;
  }
</style>
