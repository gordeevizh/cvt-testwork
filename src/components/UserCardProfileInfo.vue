<template>
  <div class="userCardProfileInfo">
    <ul class="userCardProfileInfo__infoTitle">
      <li>Семейное положение</li>
      <li>Телефон</li>
      <li>E-mail</li>
    </ul>
    <ul class="userCardProfileInfo__infoDescription">
      <li v-if="openStatusEditor">
        <UserCardEditor
          modifer="infoEditor"
          v-focus="openStatusEditor"
          :value="maritalStatus"
          @updateField="updateMaritalStatus"
          @close="openStatusEditor=false"
        />
      </li>
      <li
        v-else
        @click="openStatusEditor=true"
      >{{maritalStatus}}</li>
      <li v-if="openPhoneEditor">
        <UserCardEditor
          modifer="infoEditor"
          v-focus="openPhoneEditor"
          :value="phone"
          @updateField="updatePhone"
          @close="openPhoneEditor=false"
        />
      </li>
      <li
        v-else
        @click="openPhoneEditor=true"
      >{{phone}}</li>
      <li v-if="openEmailEditor">
        <UserCardEditor
          modifer="infoEditor"
          v-focus="openEmailEditor"
          :value="email"
          @updateField="updateEmail"
          @close="openEmailEditor=false"
        />
      </li>
      <li
        class="userCardProfileInfo__pseudoLink"
        v-else
        @click="openEmailEditor=true"
      >{{email}}</li>
    </ul>
  </div>
</template>

<script>
import UserCardEditor from './UserCardEditor'

export default {
  name: 'UserCardProfileInfo',
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
    maritalStatus: {
      default: 'Неопределен',
      type: String
    },
    phone: {
      default: 'Отсутствует',
      type: String
    },
    email: {
      default: 'Отсутствует',
      type: String
    }
  },
  data () {
    return {
      openStatusEditor: false,
      openPhoneEditor: false,
      openEmailEditor: false
    }
  },
  methods: {
    updateMaritalStatus (newStatus) {
      this.$emit('updateMaritalStatus', newStatus)
    },
    updatePhone (newPhone) {
      this.$emit('updatePhone', newPhone)
    },
    updateEmail (newEmail) {
      this.$emit('updateEmail', newEmail)
    }
  }
}
</script>

<style scoped>
  .userCardProfileInfo {
    display: flex;
    font-family: "Arial";
    font-size: 12px;
    line-height: 23px;
    color: black;
    margin-top: 20px;
  }
  .userCardProfileInfo__infoTitle {
    font-weight: bold;
    list-style-type: none;
    margin: 0;
    min-width: 130px;
    padding: 0;
  }
  .userCardProfileInfo__infoDescription {
    list-style-type: none;
    margin: 0;
    cursor: pointer;
  }
  .userCardProfileInfo__pseudoLink {
    color: #1574af;
    cursor: pointer;
    text-decoration: underline;
  }

  @media  (min-width: 488px) {
    .userCardProfileInfo__infoDescription {
      padding-left: 32px;
    }
  }

  @media (min-width: 0) and (max-width: 487px) {
    .userCardProfileInfo__infoDescription {
      padding-left: 10px;
      min-width: 132px;
    }
  }
</style>
