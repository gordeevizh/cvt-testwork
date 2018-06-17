<template>
  <div class="userCardAddIntrest">
    <BaseInput
      class="userCardAddIntrest__input"
      v-model="interest"
      @keyup.enter.native="addInterest()"
    />
    <BaseButton
      class="userCardAddIntrest__button"
      @click.native="addInterest()"
    >Добавить интерес</BaseButton>
  </div>
</template>

<script>
import BaseInput from './BaseInput'
import BaseButton from './BaseButton'
export default {
  name: 'UserCardAddIntrest',
  components: {
    BaseInput,
    BaseButton
  },
  data () {
    return {
      interest: ''
    }
  },
  methods: {
    addInterest () {
      if (this.interest !== '') {
        this.$emit('addInterest', this.interest)
        this.interest = ''
      }
    }
  }
}
</script>

<style scoped>
  .userCardAddIntrest {
    font-family: "Arial";
    background-color: white;
    box-sizing: border-box;
    box-shadow: 0px 1px 3px rgba(0,0,0,0.31);
    border-radius: 3px;
    display: flex;
    padding: 15px;
    margin-top: 30px;
  }
  .userCardAddIntrest__input {
    flex-basis: 200%;
  }

  @media (min-width: 488px) {
    .userCardAddIntrest {
      position: absolute;
      width: 487px;
    }
    .userCardAddIntrest__input {
      margin-right: 2em;
    }
  }

  @media (min-width: 0) and (max-width: 487px) {
    .userCardAddIntrest {
      flex-direction: column;
      position: relative;
      width: 100%;
    }
    .userCardAddIntrest__input {
      margin: 0 0 1em;
    }
  }
</style>
