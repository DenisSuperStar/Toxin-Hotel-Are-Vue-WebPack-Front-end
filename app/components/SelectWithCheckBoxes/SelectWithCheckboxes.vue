<template lang="pug">
    div(class="select-score select-score--free" :class="{active: show_list}")
        div(class="select-score__header" @click="toggleList")
            span(
                    class=`
                        select-score__current 
                        select-score__current--bold 
                        select-score__current--uppercase
                        select-score__current--transform`
                ) {{placeholder}}
            div(
                class=`
                    select-score__icon
                    select-score__icon--animated-icon`
            )
        transition(name="dropdown")
            div(class="select-score__body" v-show="show_list")
                template(v-for="option in options")
                    div(
                        class=`
                            select-score__item 
                            select-score__item--flexible 
                            select-score__item--free
                            select-score__item--colored`
                    )
                        div(class="select-score__box-mark")
                            checkbox(:check-mark="option.checked")
                        div(class="select-score__text") {{option.text}}
</template>

<script>
    import checkbox from '../Checkbox/Checkbox.vue';

    export default {
        name: 'select-with-checkboxes',
        components: {
            checkbox
        },
        data: () => {
            return {
                show_list: false
            }
        },
        methods: {
            toggleList: function() {
                this.show_list =!this.show_list;
            }
        },
        props: {
            options: {
                type: Array,
                default: []
            },
            placeholder: {
                type: String,
                default: 'Добавьте комфорта'
            }
        }
    }
</script>

<style lang="scss">
    @import '../../mixinSelect.scss';
    @import '../../mixinApp.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .broken {
        border: none;
    }

    .select-score {
        &--free {
            @extend .broken;
        }
        &__current {
            &--bold {
                font-weight: bold;
                color: #1f2041; 
            }
            &--uppercase {
                text-transform: uppercase;
            }
            &--transform {
                font-size: 12px;
                line-height: 15px;
                font-family: $app_font;
            }
        }
        &__text {
            margin-right: auto;
        }
        &__item {
            &--flexible {
                @include flexible(space-between, center);
            }
            &--free {
                @extend .broken;
            }
        }
    }
</style>