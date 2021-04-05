<template lang="pug">
    div(
        class="select-with-counter" 
        :class="{active: show_dropdown}"
    )
        div(
            class="select-with-counter__header" 
            @click.self="toggleDropdown"
        )
            span(
                class=`
                    select-with-counter__current 
                    select-with-counter__current--narrow`
            ) {{placeholder}}
            div(
                class=`
                    select-with-counter__icon
                    select-with-counter__icon--animated-icon`
            )
        transition(name="dropdown")
            div(
                class=`
                    select-with-counter__body 
                    select-with-counter__body--invisible`
            )
                template(v-for="(option, index) in options")
                    div(
                        class=`
                            select-with-counter__item 
                            select-with-counter__item--flexible
                            select-with-counter__item--transform
                            select-with-counter__item--bold
                            select-with-counter__item--colored`
                    )
                        span(class="select-with-counter__option") {{option.name}}
                        div(class="select-with-counter__counter")
                            span(class="select-with-counter__dec" ref="dec" @click="option.count -= 1") -
                            span(
                                    class="select-with-counter__value reset" 
                                    :class="[{'is-value-danger': option.count < 0}, {'is-value-primary': option.count > 0}]" 
                                    @click="resetCounter"
                                ) {{option.count}}
                            span(class="select-with-counter__inc" ref="inc" @click="option.count += 1") + 
</template>

<script>
    export default {
        name: 'select_with_counter',
        data: () => {
            return {
                show_dropdown: false
            }
        },
        methods: {
            toggleDropdown: function() {
                this.show_dropdown = !this.show_dropdown;
            },
            resetCounter: function() {
                this.$refs.dec.innerHTML = 0;
                this.$refs.inc.innerHTML = 0;
            }
        },
        props: {
            options: {
                type: Array,
                default: []
            },
            placeholder: {
                type: String,
                default: 'Количество спален и кроватей'
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../../mixinGlobal.scss';
    @import '../../select.scss';
    @import '../SelectCounter/mixinSelectCounter.scss';
    @import '../SelectCounter/optionsSelectCounter.scss';

    .select-with-counter {
        font-family: $app_font;
        &__current {
            &--narrow {
                width: $placeholder_narrow;
            }
        }
        &__body {
            &--invisible {
                display: none;
            }
        }
        &.active &__body {
            &--invisible {
                display: block;
                z-index: 8;
            }
        }
        &__item {
            @include currentItem(
                $item_bold,
                $item_size-text,
                $item_line-height,
                $item_color,
                $item_text_transform
            );
            &--flexible {
                @include flexible(space-between, center);
            }
            &--transform {
                padding: 0 0 0 15px;
            }
            &--colored:hover {
                color: inherit;
            }
        }
        &__item--colored:hover &__option,
        &__item--colored:hover &__value {
            color: $item_color_hovered;
            background: $item_background_hovered;
        }
        /*
            This block with styles of elements
            only in this component
        */
        &__counter {
            display: flex;
            justify-content: space-between;
            padding: 13px 15px 0 0;
            margin: 0 0 22px 0;
            &:last-child {
                margin: 0 0 8px 0;
            }
        }
        &__option {
            @include flexible(center, center);
            @include currentItem(
                $item_bold,
                $item_size-text,
                $item_line-height,
                $item_color,
                $item_text_transform
            );
            @include slice();
        }
        &__dec,
        &__inc {
            @include flexible(center, center);
            @include buttonInc(
                $inc_width,
                $inc_height,
                $inc_background,
                $inc_round,
                $inc_border-width,
                $inc_border-style,
                $inc_border-color,
                $inc_font-size,
                $inc_line-height,
                $inc_color
            );
            cursor: pointer;
            @include slice();
        }
        &__value {
            @include flexible(center, center);
            @include buttonInc(
                $value_width,
                $value_height,
                $value_background,
                $value_round,
                $value_border-thick,
                $value_border-style,
                $value_border-color,
                $value_font-size,
                $value_line-height,
                $value_color
            );
            text-transform: $value_transform;
            padding: 0;
            @include slice();
            cursor: pointer;
        }
        &__value.is-value-primary {
            color: $value_primary;
        }
        &__value.is-value-danger {
            color: $value_danger;
        }
    }
</style>