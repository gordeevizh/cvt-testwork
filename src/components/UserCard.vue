<template>
  <div class="userCard">
    <UserCardNavigation
      :tabs="tabs"
      :activeTab="activeTab"
      @switchActiveTab="switchActiveTab"
    />
    <div class="userCard__card">
      <component
        :is="activeCard"
        :friends="friends"
      />
    </div>
  </div>
</template>

<script>
import UserCardNavigation from './UserCardNavigation'
import UserCardProfile from './UserCardProfile'
import UserCardFriends from './UserCardFriends'

import axios from 'axios'
require('es6-promise').polyfill()

export default {
  name: 'UserCard',
  components: {
    UserCardNavigation,
    UserCardProfile,
    UserCardFriends
  },
  data () {
    return {
      tabs: ['Профиль', 'Друзья пользователя'],
      activeTab: 'Друзья пользователя',
      friends: []
    }
  },
  created () {
    this.loadFriends()
  },
  computed: {
    activeCard () {
      if (this.activeTab === 'Профиль') return 'UserCardProfile'
      return 'UserCardFriends'
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
