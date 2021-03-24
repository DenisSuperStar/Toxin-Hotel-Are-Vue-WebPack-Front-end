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
                    social(:social-icon="social")
</template>

<script>
    import copyright from '../Copyright/Copyright.vue';
    import navigation from '../Navigation/Navigation.vue';
    import social from '../Social/Social.vue';

    export default {
        name: 'basement',
        components: {
            copyright,
            navigation,
            social  
        },
        data: () => {
            return {
                socials: [
                    {link: '//twitter.com', key_class: 'social__icon--twed'},
                    {link: '//facebook.com', key_class: 'social__icon--fbed'},
                    {link: '//vk.com', key_class: 'social__icon--vked'}
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
        min-width: $footer_min-width;
        width: $footer_width;
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
        &__social-box {
            display: flex;
            margin: 0;
            list-style: none;
            background: #fff;
        }
    }
</style>