<template lang="pug">
    a(href="//google.com" class="redirect-button")
        span(class="redirect-button__link") {{redirect_link_text}}
</template>

<script>
    export default {
        name: 'redirect_button',
        data: () => {
            return {
                redirect_link_text: 'Смотреть отзывы'
            }
        }
    }
</script>

<style lang="scss" scoped>
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
            color: #fff;
            /*
                border thick
            */
            margin: 2px;
            /*
                inside indents
            */
            padding: 6px;
            background: linear-gradient(180deg, #bc9cff 0, #8ba4f9 100%);
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
    }
</style>