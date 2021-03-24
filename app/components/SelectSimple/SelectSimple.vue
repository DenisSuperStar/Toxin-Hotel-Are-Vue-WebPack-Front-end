<template lang="pug">
    div(class="simple-select" @click="toggleDropdown" :class="[{active: show_dropdown}, master]")
      div(class="simple-select__header")
        span(class="simple-select__current" ref="placeholder") {{placeholder}}
        div(
          class=`
            simple-select__icon 
            simple-select__icon--animated-icon`
        )
      transition(name="dropdown")
        div(class="simple-select__body" v-show="show_dropdown")
          template(v-for="(option, index) in options")
            div(
              class=`
                simple-select__item
                simple-select__item--colored` 
              @click="selectOption(option)"
            ) {{option}}
</template>

<script>
    export default {
      name: 'simple-select',
      data: () => {
        return {
          show_dropdown: false
        }
      },
      methods: {
        toggleDropdown: function() {
          this.show_dropdown =!this.show_dropdown;
        },
        selectOption: function(option) {
          this.$refs.placeholder.innerHTML = option;
        }
      },
      props: {
        options: {
          type: Array,
          default: []
        },
        placeholder: {
          type: String,
          default: 'Выберите что-нибудь'
        },
        master: {
          type: String,
          default: ''
        }
      }
    }
</script>

<style lang="scss" scoped>

  @import '../../mixinSelect.scss';

  .simple-select {
    &.active {
      z-index: 8;
    }
    &.first {
      z-index: 10;
    }
    &__body.open-list &__item:first-child {
      border-top: 1px solid rgba(31, 32, 65, 0.25);
    }
  }  
</style>