<template lang="pug">
    footer(class="footer")
        div(
            class=`
                footer__navigation-box 
                footer__navigation-box--limited 
                footer__navigation-box--decorated`
        )
            navigation
        div(class="footer__client-box")
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
        &__navigation-box {
            @include flexible(space-between, center);
            width: 100%;
            background: #fff;
            &--limited {
                border-top-width: 1px;
                border-top-style: solid;
                border-top-color: rgba(31, 32, 65, 0.1);

                border-bottom-width: 1px;
                border-bottom-style: solid;
                border-bottom-color: rgba(31, 32, 65, 0.1);
            }
            &--decorated {
                box-shadow: 0 1px rgba(31, 32, 65, 0.1);
            }
        }
        &__client-box {
            display: flex;
            width: 100%;
            justify-content: space-between;
            align-items: center;
            background: #fff;
            box-shadow: 0 10px 20px rgba(31, 32, 65, 0.05);
            padding: 26px 140px;
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