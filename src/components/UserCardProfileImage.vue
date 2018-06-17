<template>
  <div class="userCardProfileImage">
    <img
      class="userCardProfileImage__img"
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
  }
}
</script>

<style scoped>
  .userCardProfileImage {
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
    z-index: 10;
  }

  @media  (min-width: 488px) {
    .userCardProfileImage {
      width: 132px;
    }
  }

  @media  (min-width: 0) and (max-width: 487px) {
    .userCardProfileImage {
      width: 100%;
    }
    .userCardProfileImage__img {
      width: 100%;
      top: -50%;
      position: absolute;
    }
  }
</style>
