<template>
  <div class="userCardProfile">
    <div class="userCardProfile__colLeft">
      <UserCardProfileImage :imgUrl="user.avatarUrl"/>
      <UserCardProfileButton/>
    </div>
    <div class="userCardProfile__colRight">
      <UserCardProfileTitle
        :userName="user.fullName"
        :address="user.address"
        @updateUserName="updateUserName"
      />
      <UserCardProfileInfo
        :maritalStatus="user.maritalStatus"
        :phone="user.phone"
        :email="user.email"
        @updateMaritalStatus="updateMaritalStatus"
        @updatePhone="updatePhone"
        @updateEmail="updateEmail"
      />
      <UserCardProfileInterests
        :interests="user.interests"
        @removeInterest="removeInterest"
      />
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
  props: {
    user: {
      default () {
        return {}
      },
      type: Object
    }
  },
  methods: {
    removeInterest (interestIndex) {
      this.$emit('removeInterest', interestIndex)
    },
    updateUserName (newName) {
      this.$emit('updateUserName', newName)
    },
    updateMaritalStatus (newStatus) {
      this.$emit('updateMaritalStatus', newStatus)
    },
    updatePhone (newPhone) {
      this.$emit('updatePhone', newPhone)
    },
    updateEmail (newEmail) {
      this.$emit('updateEmail', newEmail)
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
