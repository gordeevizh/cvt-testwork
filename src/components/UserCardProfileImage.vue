<template>
  <div class="userCardProfileImage">
    <img
      alt="Аватар"
      :src="imgUrl"
    />
  </div>
</template>

<script>
export default {
  name: 'UserCardProfileImage',
  props: {
    imgUrl: {
      default: '/static/img/DefaultUserPic.png',
      type: String
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
  .userCardProfileImage {
    width: 132px;
    height: 169px;
    position: relative;
    border-radius: 3px;
    overflow: hidden;
  }
  .userCardProfileImage::before {
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    box-shadow: inset 0 0 6px -2px rgba(0,0,0,.32);
  }
</style>
