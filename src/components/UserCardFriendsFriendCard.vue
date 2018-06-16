<template>
  <div class="userCardFriendsFriendCard">
    <img
      class="userCardFriendsFriendCard__image"
      alt="Аватар"
      :src="friend.imgUrl"
    />
    <div class="userCardFriendsFriendCard__info">
      <div class="userCardFriendsFriendCard__title">
        <div class="userCardFriendsFriendCard__fullName">{{friend.fullName}}</div>
        <div class="userCardFriendsFriendCard__address">{{friend.address}}</div>
      </div>
      <div
        class="userCardFriendsFriendCard__state"
        v-if="friend.online"
      >Online</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserCardFriendsFriendCard',
  props: {
    friend: {
      default () {
        return {
          imgUrl: '/static/img/DefaultFriend.png',
          fullName: 'Константин Константинопольский',
          address: 'Адрес не указан',
          online: true
        }
      },
      type: Object
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCardFriendsFriendCard {
    display: flex;
    width: 50%;
  }
  .userCardFriendsFriendCard__image {
    width: 62px;
    height: 62px;
  }
  .userCardFriendsFriendCard__info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 62px;
    margin: 0 17px;

  }
  .userCardFriendsFriendCard__fullName {
    font-size: 13px;
    font-weight: bold;
    color: #1574af;
    margin-bottom: 5px;
    text-decoration: underline;
  }
  .userCardFriendsFriendCard__address {
    font-size: 11px;
    color: #373737;
  }
  .userCardFriendsFriendCard__state {
    font-size: 10px;
    font-style: italic;
    color: #2f8a26;
  }
</style>
