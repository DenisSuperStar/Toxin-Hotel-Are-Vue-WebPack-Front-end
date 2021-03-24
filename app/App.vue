<template lang="pug">
    div(id='app')
        site_header
        site_content
        site_footer
</template>

<script>
    import site_header from '../app/components/Header/Header.vue';
    import site_content from '../app/components/MiddleArea/MiddleArea.vue';
    import site_footer from '../app/components/Footer/Footer.vue';

    export default {
        name: 'app',
        components: {
            site_header,
            site_content,
            site_footer
        }
    }
</script>

<style lang="scss">
    /*Указываем box-sizing*/
    *,
    *::before,
    *::after {
        box-sizing: border-box;
    }

    *:focus {
        outline: none;
    }
    /*Настройки по умолчанию для body*/
    body {
        min-height: 100vh;
        scroll-behavior: smooth;
    }
    /*Убираем внутренние отступы*/
    ul,
    li {
        padding: 0;
    }
    /*Убираем внешние отступы*/
    .page,
    h1,
    h2,
    h3,
    h4,
    p,
    ul,
    li {
        margin: 0;
    }
    /*Убираем стандартную стилизацию для всех ul, li*/
    ul,
    li {
        list-style: none;
    }
    /*Ссылки без класса сбрасываем до дефолтных стилей*/
    a:not([class]) {
        text-decoration-skip-ink: auto;
    }
    /*Упрощаем работу с изображениями*/
    img {
        display: block;
        max-width: 100%;
    }
    /*Наследуем шрифты для инпутов и кнопок*/
    input,
    button {
        font: inherit;
    }

    .close-list {
        display: none;
        border: none;
        opacity: 1;
        &:hover {
            opacity: 1 !important;
        }
    }

    .open-list {
        display: block;
    }

    .subheader-animate {
        &__break.share:hover > &__character {
            color: #fff;
            background: #fff;
            transition: all 0.2s ease-in-out;
            &::after {
                width: 100%;
                background: linear-gradient(180deg, #bc9cff 0, #8ba4f9 100%);
            }
        } 
        &__character {
            display: block;
            position: relative;
            margin-right: -0.47px;
            text-transform: uppercase;
            color: #1f2041;
            font: bold 12px / 15px 'Montserrat', sans-serif;
            &::after {
                content: "";
                position: absolute;
                top: 0;
                left: 0;
                width: 0;
                height: 100%;
                transition: all 0.5s ease-in-out;
                z-index: -5;
            }
            &--spaced {
                margin-right: 5px;
            }
        }
    }

    $start: 1;
    $finish: 25;

    @for $j from $start to $finish {
       .subheader-animate {
           &__break.share:hover > &__character:nth-child(#{$j})::after {
               $delay: 100 * $j;
               transition-delay: $delay + ms;
           }
           &__break.share:hover > &__character:nth-child(#{$j}) {
               $delay_copy: 110 * $j;
               $rotation: ($j * 0.01);
               transition-delay: $delay_copy + ms;
               transform: rotate($rotation + deg);
           }
       } 
    }
</style>