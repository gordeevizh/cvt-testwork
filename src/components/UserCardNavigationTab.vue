<template>
  <button class="userCardNavigationTab">{{tabText}}</button>
</template>

<script>
export default {
  name: 'UserCardNavigationTab',
  props: {
    tabText: {
      default: '',
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
  .userCardNavigationTab {
    background-image: linear-gradient(0deg, #1f68ac 0%, #0685b4 100%);
    border: none;
    border-radius: 3px 3px 0 0;
    cursor: pointer;
    height: 32px;
    margin-right: 10px;
    font-family: "Arial";
    font-size: 14px;
    line-height: 21px;
    color: white;
    outline: none;
    position: relative;
    text-shadow: 0px -1px 0px rgba(0,0,0,0.38);
  }
  .userCardNavigationTab.active {
    background: white;
    box-shadow: 0px 1px 3px rgba(0,0,0,0.31);
    color: black;
    text-shadow: none;
  }
  .userCardNavigationTab.active::after {
    content: '';
    background: white;
    bottom: -5px;
    width: 110%;
    height: 5px;
    position: absolute;
    left: 0;
  }
</style>
