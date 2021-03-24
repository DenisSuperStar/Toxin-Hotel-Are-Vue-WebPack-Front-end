<template lang="pug">
    li(class="social")
        a(:href="socialIcon.link" class="social__link")
            span(class="social__icon" :class="socialIcon.key_class")
</template>

<script>
    export default {
       name: 'Social',
       props: ['socialIcon']
    }
</script>

<style lang="scss" scoped>
    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .social {
        display: block;
        margin: 0 20px 0 0;
        &__link,
        &__link:hover {
            text-decoration: none;
        }
        &__icon {
            @include flexible(center, center);
            width: 24px;
            height: 24px;
            color: #fff;
            font-size: 24px;
            line-height: 23px;
            font-family: 'Font Awesome 5 Pro';
            cursor: pointer;
            &--twed::after,
            &--fbed::after,
            &--vked::after {
                color: #8ba4f9;
            }
            &--twed::after {
                content: '\f099';
            }
            &--fbed::after {
                content: '\f082';
            }
            &--vked::after {
                content: '\f16d'
            }
        }
    }

    .social__icon--twed::after {
        color: #8ba4f9;
        content: '\f099';
        font-family: 'Font Awesome 5 Pro';
        font-weight: bold;
    }
</style>

