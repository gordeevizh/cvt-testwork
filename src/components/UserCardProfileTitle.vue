<template>
  <div class="userCardProfileTitle">
    <UserCardEditor
      modifer="nameEditor"
      v-if="openNameEditor"
      v-focus="openNameEditor"
      :value="userName"
      @updateField="updateUserName"
      @close="openNameEditor=false"
    />
    <h1
      class="userCardProfileTitle__userName"
      v-else
      @click="openNameEditor=true"
    >{{userName}}</h1>
    <p class="userCardProfileTitle__address">{{address}}</p>
  </div>
</template>

<script>
import UserCardEditor from './UserCardEditor'

export default {
  name: 'UserCardProfileTitle',
  components: {
    UserCardEditor
  },
  directives: {
    focus: {
      inserted: function (el, binding) {
        if (binding.value) {
          el.firstChild.focus()
        }
      }
    }
  },
  props: {
    userName: {
      default: 'Безымянный',
      type: String
    },
    address: {
      default: 'Адрес не указан',
      type: String
    }
  },
  data () {
    return {
      openNameEditor: false
    }
  },
  methods: {
    updateUserName (newName) {
      this.$emit('updateUserName', newName)
    }
  }
}
</script>

<style scoped>
  .userCardProfileTitle {
  }
  .userCardProfileTitle__userName {
    color: black;
    font-family: "Arial";
    font-size: 23px;
    font-weight: normal;
    line-height: 21px;
    margin: 0;
    cursor: pointer;
  }
  .userCardProfileTitle__address {
    color: #757575;
    font-family: "Arial";
    font-size: 11px;
    line-height: 21px;
    margin: 0;
  }
</style>
