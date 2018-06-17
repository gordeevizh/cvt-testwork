<template>
  <div class="userCardEditor">
    <BaseInput
        class="userCardEditor__input"
        :class="modifer"
        :value="value"
        @input="updateResultValue"
        @focus="updateResultValue"
        @keyup.enter.native="closeAndUpdate()"
        @blur="closeAndUpdate()"
      />
  </div>
</template>

<script>
import BaseInput from './BaseInput'

export default {
  name: 'UserCardEditor',
  components: {
    BaseInput
  },
  props: {
    value: {
      default: '',
      type: String
    },
    modifer: {
      default: '',
      type: String
    }
  },
  data () {
    return {
      resultValue: ''
    }
  },
  methods: {
    updateResultValue (value) {
      this.resultValue = value
    },
    updateField () {
      if (this.resultValue !== this.value) {
        this.$emit('updateField', this.resultValue)
      }
    },
    close () {
      this.$emit('close')
    },
    closeAndUpdate () {
      this.close()
      this.updateField()
    }
  }
}
</script>

<style scoped>
  input.nameEditor {
    height: 21px;
  }
  input.infoEditor {
    height: 23px;
  }
</style>
