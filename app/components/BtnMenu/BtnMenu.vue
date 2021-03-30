<template lang="pug">
    div(
        class="btn-account" 
        :class="selectedItem"
    )
        a(
            href="//google.com" 
            class="btn-account__link"
        ) {{btnText}}
</template>

<script>
    export default {
        name: 'just_btn',
        props: {
            selectedItem: String,
            btnText: String
        },
    }
</script>

<style lang="scss" scoped>

    .btn-account {
        & > &__link {
            display: flex;
            justify-content: center;
            align-items: center;
            text-decoration: none;
            text-transform: uppercase;
            font-weight: bold;
            font-size: 12px;
            line-height: 15px;
            font-family: 'Montserrat', sans-serif;
        }
        &.is-small,
        &.is-large {
            position: relative;
        }
        &.is-small {
            z-index: 1;
            width: 87px;
            height: 34px;
        }
        &.is-small,
        &.is-large,
        &.is-small > &__link,
        &.is-large > &__link {
            &,
            &::before {
                border-radius: 22px;
            }
        }
        &.is-small,
        &.is-small > &__link {
            background: #fff;
            color: #8ba4f9;
        }
        &.is-small > &__link,
        &.is-large > &__link {
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
        }
        &.is-small > &__link::before {
            content: '';
            position: absolute;
            z-index: -1;
            top: -2px;
            right: -2px;
            bottom: -2px;
            left: -2px;
            background: linear-gradient(180deg, #bc9cff 100%, #8ba4f9 100%);
        }
        &.is-large {
            width: 196px;
            height: 34px;
        }
        &.is-large,
        &.is-large > &__link {
            background: linear-gradient(180deg, #bc9cff 0, #8ba4f9 100%);
        }
        &.is-large > &__link {
            color: #fff;
        }
    }
</style>