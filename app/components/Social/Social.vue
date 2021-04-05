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
    @import '../Social/optionsSocial.scss';

    .social-icon {
        width: max-content;
        background: $social_background;
        &__link,
        &__link:hover {
            display: block;
            font-size: $social_size;
            background: $social_background-hover;
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
                background: $social_animate;
                border-radius: $social_animate_round;
                transition: all 0.5s ease-in-out;
                animation: jelly 0.75s ease forwards;
            }
        }
    }

    @keyframes jelly {
        0%, 20% {
            transform: scale(1);
            border-radius: $social_start_animate_round;
            background: $social_start_animate_background;
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
            border-radius: $social_end_animate_round;
        }
    }
</style>

