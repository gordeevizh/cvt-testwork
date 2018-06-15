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
      />
    </div>
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
      tabs: ['Профиль', 'Друзья пользователя'],
      activeTab: 'Профиль',
      cards: ['UserCardProfile', 'UserCardNavigation']
    }
  },
  computed: {
    activeCard () {
      if (this.activeTab === 'Профиль') return 'UserCardProfile'
      return 'UserCardNavigation'
    }
  },
  methods: {
    switchActiveTab (tabName) {
      this.activeTab = tabName
    }
  }
}
</script>

<style scoped>
  .userCard__card {
    width: 487px;
    min-height: 278px;
    background-color: white;
    box-shadow: 0px 1px 3px rgba(0,0,0,0.31);
    border-radius: 3px;
  }
</style>
