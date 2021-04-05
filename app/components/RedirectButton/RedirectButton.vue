<template lang="pug">
    a(href="//google.com" class="redirect-button")
        span(class="redirect-button__link" :class="{'is-even': this.firefox}") {{redirect_link_text}}
</template>

<script>
    export default {
        name: 'redirect_button',
        data: () => {
            return {
                redirect_link_text: 'Смотреть отзывы',
                firefox: false
            }
        },
        created: function() {
            /*
                define browser name
            */
            const user = window.navigator.userAgent;
            this.firefox = (user.indexOf('Firefox') !=-1);
        }
    }
</script>

<style lang="scss" scoped>
    @import '../RedirectButton/optionsRedirectButton.scss';

    .redirect-button {
        display: block;
        position: relative;
        overflow: hidden;
        cursor: pointer;
        &, &:hover {
            text-decoration: none;
        }
        & > &__link {
            display: block;
            position: relative;
            color: $redirect_color;
            /*
                border thick
            */
            margin: $redirect_border-width;
            /*
                inside indents
            */
            padding: 6px;
            background: $redirect_background;
        }
        /*
            styles of animated link
        */
        &::before,
        &::after {
            content: "";
            position: absolute;
        }
        &::before {
            content: "";
            /*
                if it doesn't exist then it will be another animation
            */
            top: 0;
            left: 0;
            bottom: 0;
            background: #fff;
            /*
                glide forward motion
            */
            transform: translateX(-300px);
            transition: transform 0.95s ease-in-out;
        }
        &::after,
        &:hover::after {
            transition: width 0.5s ease-in-out;
        }
        &:hover::before {
            /*
                The animation will not working without this css rule
            */
            width: 100%;
            transform: translateX(0);
        }
        /*
            firefox tweak
        */
        & > &__link.is-even {
            margin-top: $redirect_border-width + 1px;
            margin-right: $redirect_border-width;
            margin-bottom: $redirect_border-width;
            margin-left: $redirect_border-width;
        }
    }
</style>