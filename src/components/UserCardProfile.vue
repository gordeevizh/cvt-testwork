<template>
  <div class="userCardProfile">
    <div class="userCardProfile__colLeft">
      <UserCardProfileImage/>
      <UserCardProfileButton/>
    </div>
    <div class="UserCardProfile__colRight">
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
    width: 487px;
    height: 278px;
    background-color: white;
    display: flex;
  }
  .userCardProfile__colLeft {
    margin: 15px;
  }
  .UserCardProfile__colRight {
    margin: 15px 15px 15px 5px;
  }
</style>
