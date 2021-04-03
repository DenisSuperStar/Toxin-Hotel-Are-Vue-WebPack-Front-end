<template lang="pug">
    header(
        class=`
            header 
            header--slow-motion
            `
            @scroll="move"
            :class="{'is-sticky': action}"
    )
        box_header
</template>

<script>
    import box_header from '../HeaderContent/HeaderContent.vue';

    export default {
        name: 'site_header',
        components: {
            box_header
        },
        data: function() {
            return {
                action: false
            }
        },
        methods: {
            move: function() {
                this.action != this.action;
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../TheHeader/mixinHeader.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    /*
        Добавить обработчик события scroll
    */

    .header {
        @include flexible(space-between, center);
        padding: 15px 140px;
        width: $header_width;
        min-width: $header_min-width;
        background: $header_background;
        box-shadow: none;
        &--slow-motion {
            transition: all 0.5s ease-in-out;
        }
        &.is-sticky {
            position: fixed;
            border-bottom-left-radius: $header_round;
            border-bottom-right-radius: $header_round;
            cursor: pointer;
            z-index: 11;
            &:hover {
               box-shadow: 0 10px 20px $header_shadow-color; 
            }
            &:hover::after {
                background: $header_background;
                opacity: 0;
                transform: scaleX(1.4) scaleY(1.6);
            }
            &::after {
                content: '';
                display: block;
                width: 100%;
                position: absolute;
                top: 0;
                bottom: 0;
                left: 0;
            }
        }
        &--slow-motion.is-sticky {
            transition: all 1s ease;
        }
    }

    /*
        max adaptibility the header
    */
    @media screen and (max-width: 767px) {
        .header {
            @include flexible(space-between, flex-start);
            padding: 15px 24px;
        }
    }

    @media screen and (min-width: 768px) and (max-width: 1199px) {
        .header {
            padding: 15px 30px;
        }
    }

    @media screen and (min-width: 960px) and (max-width: 1199px) {
        .header.is-sticky {
            padding: 0 30px;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1399px) {
        .header {
            & {padding: 15px 70px 15px 30px;}
            &.is-sticky {padding: 0 70px 0 30px;}
        }
    }

    @media screen and (min-width: 1400px) and (max-width: 1470px) {
        .header {
            & {padding: 15px 140px;}
            &.is-sticky {padding: 0 140px;}
        }
    }

    @media screen and (min-width: 1471px) {
        .header.is-sticky {
            padding: 0 140px;
        }
    }
</style>