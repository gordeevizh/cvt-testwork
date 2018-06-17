<template>
  <div class="userCardFriends">
    <CustomScroll>
      <UserCardFriendsFriendCard
        v-for="friend in friends"
        :key="friend.id"
        :friend="friend"
      />
    </CustomScroll>
  </div>
</template>

<script>
import CustomScroll from './CustomScroll'
import UserCardFriendsFriendCard from './UserCardFriendsFriendCard'

export default {
  name: 'UserCardFriends',
  components: {
    CustomScroll,
    UserCardFriendsFriendCard
  },
  props: {
    friends: {
      default () {
        return []
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
  .userCardFriends {
    display: flex;
    flex-wrap: wrap;
    padding: 15px 12px 15px 15px;
    background: white;
    width: 100%;
    height: 278px;
    box-sizing: border-box;
  }
</style>
