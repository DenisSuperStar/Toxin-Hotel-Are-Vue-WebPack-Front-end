<template lang="pug">
    header(class="header")
        box_header
</template>

<script>
    import box_header from '../HeaderContent/HeaderContent.vue';

    export default {
        name: 'site_header',
        components: {
            box_header
        },
    }
</script>

<style lang="scss" scoped>
    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .header {
        @include flexible(space-between, center);
        padding: 15px 140px;
        min-width: 350px;
        width: 100%;
        height: max-content;
        background: #fff;
        transition: all 0.5s ease-in-out;
    }

    @media screen and (min-width: 960px) {
        .sticky {
            position: fixed;
            background: #fff;
            box-shadow: none;
            border-bottom-left-radius: 4px;
            border-bottom-right-radius: 4px;
            transition: all 0.5s ease-in-out;
            z-index: 9999;
            cursor: pointer;
            &:hover {
                box-shadow: 0 10px 20px rgba(31, 32, 65, .24);
                &::after {
                    background: #fff;
                    opacity: 0;
                    transform: scaleX(1.4) scaleY(1.6);
                }
            }
            &::after {
                content: '';
                display: block;
                width: 100%;
                position: absolute;
                top: 0;
                bottom: 0;
                left: 0;
                transition: all 1s ease;
            }
        }
    }

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
        .sticky {
            padding: 0 30px;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1399px) {
        .header {
            padding: 15px 70px 15px 30px;
        }

        .sticky {
            padding: 0 70px 0 30px;
        }
    }

    @media screen and (min-width: 1400px) and (max-width: 1470px) {
        .header {
            padding: 15px 140px;
        }

        .sticky {
            padding: 0 140px;
        }
    }

    @media screen and (min-width: 1471px) {
        .sticky {
            padding: 0 140px;
        }
    }
</style>