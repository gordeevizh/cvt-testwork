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
    box-sizing: border-box;
  }

  @media  (min-width: 488px) {
    .userCardFriends {
      height: 278px;
    }
  }

  @media  (min-width: 0) and (max-width: 487px) {
    .userCardFriends {
      height: auto;
    }
  }
</style>
