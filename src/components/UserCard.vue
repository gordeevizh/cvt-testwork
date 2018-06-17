<template>
  <div class="userCard" v-show="show">
    <UserCardNavigation
      :tabs="tabs"
      :activeTab="activeTab"
      @switchActiveTab="switchActiveTab"
    />
    <div class="userCard__card">
      <component
        :is="activeCard.name"
        v-bind="activeCard.props"
        @removeInterest="removeUserInterest"
        @updateUserName="updateUserName"
        @updateMaritalStatus="updateMaritalStatus"
        @updatePhone="updatePhone"
        @updateEmail="updateEmail"
      />
    </div>
    <UserCardAddIntrest
      v-if="activeTab === 'Профиль'"
      @addInterest="addUserInterest"
    />
  </div>
</template>

<script>
import UserCardNavigation from './UserCardNavigation'
import UserCardProfile from './UserCardProfile'
import UserCardFriends from './UserCardFriends'
import UserCardAddIntrest from './UserCardAddIntrest'

import axios from 'axios'
require('es6-promise').polyfill()

export default {
  name: 'UserCard',
  components: {
    UserCardNavigation,
    UserCardProfile,
    UserCardFriends,
    UserCardAddIntrest
  },
  data () {
    return {
      tabs: ['Профиль', 'Друзья пользователя'],
      activeTab: 'Профиль',
      user: {},
      friends: [],
      show: false
    }
  },
  created () {
    this.loadUser()
    this.loadFriends()
  },
  updated () {
    this.$nextTick(function () {
      this.show = true
    })
  },
  computed: {
    activeCard () {
      if (this.activeTab === 'Профиль') {
        return {
          name: 'UserCardProfile',
          props: {user: this.user}
        }
      }
      return {
        name: 'UserCardFriends',
        props: {friends: this.friends}
      }
    }
  },
  methods: {
    switchActiveTab (tabName) {
      this.activeTab = tabName
    },
    loadFriends () {
      let self = this
      axios.get('/static/friends.json')
        .then(function (response) {
          self.friends = response.data
        })
        .catch(function (error) {
          console.log(error)
        })
    },
    loadUser () {
      let self = this
      axios.get('/static/user.json')
        .then(function (response) {
          self.user = response.data
          self.updateUserDataFromLocal()
        })
        .catch(function (error) {
          console.log(error)
        })
    },
    removeUserInterest (interestIndex) {
      this.user.interests.splice(interestIndex, 1)
    },
    addUserInterest (interest) {
      this.user.interests.unshift(interest)
    },
    updateUserName (newName) {
      this.user.fullName = newName
      this.saveToLocal('fullName', newName)
    },
    updateMaritalStatus (newStatus) {
      this.user.maritalStatus = newStatus
      this.saveToLocal('maritalStatus', newStatus)
    },
    updatePhone (newPhone) {
      this.user.phone = newPhone
      this.saveToLocal('phone', newPhone)
    },
    updateEmail (newEmail) {
      this.user.email = newEmail
      this.saveToLocal('email', newEmail)
    },
    saveToLocal (key, value) {
      value = JSON.stringify(value)
      localStorage.setItem(key, value)
    },
    loadFromLocal (key) {
      return JSON.parse(localStorage.getItem(key))
    },
    updateUserDataFromLocal () {
      if ('fullName' in localStorage) { this.user.fullName = this.loadFromLocal('fullName') }
      if ('maritalStatus' in localStorage) { this.user.maritalStatus = this.loadFromLocal('maritalStatus') }
      if ('phone' in localStorage) { this.user.phone = this.loadFromLocal('phone') }
      if ('email' in localStorage) { this.user.email = this.loadFromLocal('email') }
    }
  }
}
</script>

<style scoped>
  .userCard__card {
    font-family: "Arial";
    width: 487px;
    min-height: 278px;
    background-color: white;
    box-shadow: 0px 1px 3px rgba(0,0,0,0.31);
    border-radius: 3px;
  }
</style>
