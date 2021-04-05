<template lang="pug">
    div(class="select-with-counter" :class="{active: show_dropdown}")
        div(class="select-with-counter__header" @click.self="toggleDropdown")
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
                                    :class="[{'value-danger': option.count < 0}, {'value-primary': option.count > 0}]" 
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
    @import './mixinSelectWithCounter.scss';

    .select-with-counter {
        &__current {
            &--narrow {
                width: $select-header_width_narrow;
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
            &--flexible {
                @include flexible(space-between, center);
            }
            &--transform {
                font-size: $select-header_text_size;
                line-height: $select-header_text_height;
                font-family: $app_font;
                text-transform: $select-header_type_text;
                padding: 0 0 0 15px;
            }
            &--bold {
                font-weight: $select-header_text_weight;
                color: $select-header_color_weight;
            }
            &--colored:hover {
                color: inherit;
            }
        }
        &__item--colored:hover &__option,
        &__item--colored:hover &__value {
            color: $select-item_color_hovered;
            background: $select-item_background_hovered_colored;
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
            font: bold 12px / 15px 'Montserrat', sans-serif;
            text-transform: uppercase;
            color: #1f2041;
            @include slice();
        }
        &__dec,
        &__inc {
            @include flexible(center, center);
            width: 30px;
            height: 30px;
            background: #fff;
            border-radius: 22px;
            border: 1px solid rgba(31, 32, 65, 0.25);
            font: 18px / 22px 'Montserrat', sans-serif;
            color: rgba(31, 32, 65, 0.5);
            cursor: pointer;
            @include slice();
        }
        &__value {
            @include flexible(center, center);
            width: 30px;
            height: 30px;
            background: transparent;
            border: none;
            font: bold 12px / 15px 'Montserrat', sans-serif;
            padding: 0;
            color: #1f2041;
            text-transform: uppercase;
            cursor: pointer;
            @include slice();
        }
    }

    .value-danger {
        color: rgba(220, 53, 69, 0.5);
    }

    .value-primary {
        color: #8ba4f9;
    }
</style>