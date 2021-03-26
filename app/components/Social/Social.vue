<template lang="pug">
    div(class="social-icon")
        a(
            :href="iconLink" 
            class=`
                social-icon__link
                social-icon__link--animated
            ` 
            :class="iconName"
        )
</template>

<script>
    export default {
        name: 'social_icon',
        props: {
            iconLink: {
                type: String,
                default: ''
            },
            iconName: {
                type: String,
                default: ''
            }
        }
    }
</script>

<style lang="scss" scoped>

    .social-icon {
        width: max-content;
        background: linear-gradient(180deg, #bc9cff 100%, #8ba4f9 100%);
        &__link,
        &__link:hover {
            display: block;
            font-size: 24px;
            background: #fff;
            text-decoration: none;
            mix-blend-mode: screen;
        }
        &__link {
            &::before {
                display: block;
                font-family: 'Font Awesome 5 Brands';
            }
            &.is-twitter::before {
                content: '\f099';
            }
            &.is-facebook::before {
                content: '\f082';
            }
            &.is-vk::before {
                content: '\f16d';
            }
            &--animated:hover::before {
                padding: 20px;
                background: linear-gradient(180deg, #bc9cff 100%, #8ba4f9 100%);
                border-radius: 2px;
                transition: all 0.5s ease-in-out;
                animation: jelly 0.75s ease forwards;
            }
        }
    }

    @keyframes jelly {
        0%, 20% {
            transform: scale(1);
            border-radius: 40px;
            background: linear-gradient(180deg, #bc9cff 100%, #8ba4f9 100%);
        }
        30% {
            transform: scale(1.2);
        }
        40% {
            transform: scale(1.1);
        }
        50% {
            transform: scale(1);
            border-radius: 10px;
        }
        60%, 100% {
            transform: scale(1);
            border-radius: 5px;
        }
    }
</style>

