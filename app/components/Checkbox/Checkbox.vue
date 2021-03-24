<template lang="pug">
    label(class="cm-checkbox")
        input(type="checkbox" class="cm-checkbox__input" :checked="checkMark")
        span(class="cm-checkbox__fake")
</template>

<script>
    export default {
        name: 'checkbox',
        props: {
            checkMark: {
                type: String,
                default: ''
            }
        }
    }
</script>

<style lang="scss" scoped>

@import '../Checkbox/mixinCheckbox.scss';

@mixin flexible($align, $item) {
    display: flex;
    justify-content: $align;
    align-items: $item;
}

@mixin hidden {
    position: absolute;
    /*
        hide default appearance DOM item
        for Chrome and FireFox
    */
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
}

.cm-checkbox {
    display: flex;
    &__input {
        @include hidden();
    }
    &__input:checked + &__fake {
        animation: jellybox 0.75s ease;
        &::after {
            opacity: 1;
            transform: rotate(45deg) scale(1);
        }
    }
    &__fake {
        @include flexible(center, baseline);
        position: relative;
        width: 20px;
        height: 20px;
        /*split for ease replacement*/
        border-width: $checkbox_border_thick;
        border-style: $checkbox_border_style;
        border-color: $checkbox_border_color;
        /*checkbox ease replacement*/
        background: $checkbox_background;
        border-radius: $checkbox_self_round;
        padding: 4px 0 0 0;
        margin: 0 10px 0 0;
        cursor: pointer;
        &::after {
            content: "";
            position: absolute;
            width: 5px;
            height: 8px;
            opacity: 0;
            transform: rotate(45deg) scale(0);
            /*split border-right*/
            border-right-width: $check_mark_thick;
            border-right-style: $check_mark_style;
            border-right-color: $check_mark_color;
            /*split border-bottom*/
            border-bottom-width: $check_mark_thick;
            border-bottom-style: $check_mark_style;
            border-bottom-color: $check_mark_color;
            /*
                glide change of properties
            */
            transition: all 0.5s ease-in-out;
            transition-delay: 0.15s;
        }
    }
}

/*
    description animation
*/
@keyframes jellybox {
    0% {
        transform: scale(1, 1);
    }
    30% {
        transform: scale(1.25, 0.75);
    }
    40% {
        transform: scale(0.75, 1.25);
    }
    50% {
        transform: scale(1.15, 0.85);
    }
    65% {
        transform: scale(0.95, 1.05);
    }
    75% {
        transform: scale(1.05, 0.95);
    }
    100% {
        transform: scale(1, 1);
    }
}
</style>