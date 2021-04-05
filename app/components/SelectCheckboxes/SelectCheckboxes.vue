<template lang="pug">
    div(
        class="select-score select-score--free" 
        :class="{active: show_list}"
    )
        div(
            class="select-score__header" 
            @click="toggleList"
        )
            span(
                    class=`
                        select-score__current
                        select-score__current--free
                    `
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
    @import '../../mixinApp.scss';
    @import '../../mixinGlobal.scss';
    @import '../../select.scss';
    @import '../SelectCheckboxes/mixinSelectCheckboxes.scss';
    @import '../SelectCheckboxes/optionsSelectCheckboxes.scss';
    
    .broken {
        border: none;
    }

    .select-score {
        font-family: $app_font;
        &--free {
            @extend .broken;
        }
        &__current {
            @include currentPlaceholder(
                $placeholder_bold,
                $placeholder_size,
                $placeholder_height,
                $placeholder_color,
                $placeholder_transform
            );
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