<template lang="pug">
    footer(class="footer")
        div(
            class=`
                footer__navigation-box 
                footer__navigation-box--limited
                `
        )
            navigation
        div(
            class=`
                footer__client-box 
                footer__client-box--visual
                `
        )
            div(class="footer__info-box")
                copyright
            ul(class="footer__social-box")
                template(v-for="social in socials")
                    li(class="footer__social-item")
                        social_icon(
                            :icon-link="social.link" 
                            :icon-name="social.icon_name"
                        )
</template>

<script>
    import copyright from '../Copyright/Copyright.vue';
    import navigation from '../Navigation/Navigation.vue';
    import social_icon from '../Social/Social.vue';

    export default {
        name: 'basement',
        components: {
            copyright,
            navigation,
            social_icon  
        },
        data: () => {
            return {
                socials: [
                    {
                        link: '//twitter.com',
                        icon_name: 'is-twitter'
                    },
                    {
                        link: '//facebook.com',
                        icon_name: 'is-facebook'
                    },
                    {
                        link: '//vk.com',
                        icon_name: 'is-vk'
                    }
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../Footer/mixinFooter.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }
    .footer {
        min-width: $footer_min_width;
        width: $footer_width;
        background: $footer_background;
        &__navigation-box {
            @include flexible(space-between, center);
            &--limited {
                border-top-width: $footer_border-thick;
                border-top-style: $footer_border-style;
                border-top-color: $footer_border-color;

                border-bottom-width: $footer_border-thick;
                border-bottom-style: $footer_border-style;
                border-bottom-color: $footer_border-color;
            }
        }
        &__client-box {
            @include flexible(space-between, center);
            padding: 26px 140px;
            &--visual {
                box-shadow: 0 10px 20px $footer_shadow_color_of_custom;
            }
        }
        &__navigation-box,
        &__client-box {
            width: 100%;
        }
        &__social-box {
            display: flex;
            margin: 0;
            list-style: none;
        }
        &__social-item {
            display: block;
            padding: 0 20px;
            &:first-child,
            &:last-child {
                padding: 0;
            }
        }
    }

    @media screen and (max-width: 767px) {
        .footer {
            &__client-box {
                display: flex;
                flex-flow: column;
                padding: 26px 0;
            }
        }
    }

    @media screen and (min-width: 768px) and (max-width: 1199px) {
        .footer {
            &__client-box {
                padding: 26px 46px;
            }
        }
    }
</style>