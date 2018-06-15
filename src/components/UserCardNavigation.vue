<template>
  <div class="userCardNavigation">
    <UserCardNavigationTab
      v-for="tab in tabs"
      :key="tab.id"
      :tabText="tab"
      :class="{ active: activeTab === tab }"
      @click.native="switchActiveTab(tab)"
    />
  </div>
</template>

<script>
import UserCardNavigationTab from './UserCardNavigationTab'
export default {
  name: 'UserCardNavigation',
  components: {
    UserCardNavigationTab
  },
  props: {
    tabs: {
      default () {
        return ['tab1', 'tab2']
      },
      type: Array
    },
    activeTab: {
      default: 'tab1',
      type: String
    }
  },
  methods: {
    switchActiveTab (tab) {
      this.$emit('switchActiveTab', tab)
    }
  }

}
</script>

<style scoped>
  .userCardNavigation {
  }
</style>
