<template lang="pug">
    button(
        class="btn" 
        :class="selectedBtnClass" 
        :id="addedUniqId"
    ) {{btnText}}
</template>

<script>
    export default {
        name: 'just_btn',
        props: {
            selectedBtnClass: String,
            addedUniqId: String,
            btnText: String
        },
    }
</script>

<style lang="scss" scoped>
    /*
        Styles for all buttons
    */
    $default_rounding: 22px;
    $text_default_height: uppercase;
    $color_shadow: rgba(31, 32, 65, 0.2); 

    /*
        By default
    */
    $color_text_btn: rgba(31, 32, 65, 0.5);
    $border_default_btn: 1px solid $color_text_btn;
    $background_default_btn: #fff;
    
    /*
        For small button
    */
    $background_small_btn: $background_default_btn;
    $color_small_btn: #bc9cff;
    $border_small_btn: 2px solid $color_small_btn;

    /*
        For large button 
    */
    $background_large_btn: linear-gradient(180deg, #bc9cff 0, #8ba4f9 100%);
    $color_large_btn: #fff;
    $border_large_btn: none;

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .state-shadow {
        box-shadow: 0 5px 10px $color_shadow;
    }

    .btn,
    .btn:link,
    .btn:visited {
        position: relative;
        border-radius: $default_rounding;
        border: $border_default_btn;
        background: $background_default_btn;
        color: $color_text_btn;
        font: normal normal bold 12px / 15px 'Montserrat', sans-serif;
        text-transform: $text_default_height;
        @include slice();
        cursor: pointer;
        transition: all 0.75s ease;
    }

    .btn {
        &:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px $color_shadow;
            &::after {
                background: $background_default_btn;
                opacity: 0;
                transform: scaleX(1.4) scaleY(1.6);
            }
        }
        &:active {
            transform: translateY(-1px);
            @extend .state-shadow;
        }
        &:focus {
            outline: none;
            @extend .state-shadow;
        }
        &::after {
            content: "";
            display: block;
            width: 100%;
            height: 100%;
            border-radius: 22px;
            position: absolute;
            top: 0;
            left: 0;
            background: transparent;
            transition: all 1s ease;
        }
        &--action {
            width: 100% !important;
            height: 44px !important;
        }
        &--signed-in,
        &--signed-in:link,
        &--signed-in:visited {
            width: 87px;
            height: 34px;
            background: $background_small_btn;
            border: $border_small_btn;
        }
        &--signed-in,
        &--signed-in:link,
        &--signed-in:visited,
        &--signed-in:hover {
            color: $color_small_btn
        }
        &--signed-up,
        &--signed-up:link,
        &--signed-up:visited {
            width: 196px;
            height: 34px;
            background: $background_large_btn;
            border: $border_large_btn;
        }
        &--signed-up,
        &--signed-up:link,
        &--signed-up:visited,
        &--signed-up:hover {
            color: $color_large_btn;
        }
        &--transform {
            width: 99px;
            height: 44px;
            background: #fff;
            border: 2px solid #bc9cff;
            box-shadow: 0 0 25px rgba(0, 0, 0, 0.25);
        }
    }

    @media screen and (max-width: 1149px) {
        .btn--signed-in:not(.is-dialog),
        .btn--signed-up:not(.is-dialog) {
            width: 100%;
            height: 60%;
        }

        .btn--signed-in:not(.is-dialog),
        .btn--signed-up:not(.is-dialog) {
            font-size: 16px;
        }

        .btn--signed-in.is-dialog,
        .btn--signed-up.is-dialog {
            font-size: 14px;
        }
    }

    @keyframes waves {
        0% {
            opacity: 0;
            transform: translateY(30px)
        }
        100% {
            opacity: 1;
            transform: translateY(0px);
        }
    }

    .waves {
        animation: waves 0.5s ease-in-out backwards;
    }
</style>