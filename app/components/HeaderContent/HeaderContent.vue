<template lang="pug">
    div(class="header-box")
        div(class="header-box__site-logo")
            div(class="header-box__logo")
                logo
            div(class="header-box__logo-text")
                text_logo
        div(class="header-box__menu-box")
            div(class="header-box__humburger-box")
                humburger
            div(class="header-box__menu")
                top_menu
        div(class="header-box__buttons-box")
            div(class="header-box__btn-small")
                btn_link(
                    selected-item="is-small"
                    btn-text="Войти" 
                )
            div(class="header-box__btn-large")
                btn_link(
                    selected-item="is-large"
                    btn-text="Зарегистрироваться"
                )
                
</template>

<script>
    import btn_link from '../BtnMenu/BtnMenu.vue';
    import logo from '../Logo/Logo.vue';
    import humburger from '../HumburgerMenu/HumburgerMenu.vue'
    import top_menu from '../TopMenu/TopMenu.vue';
    import text_logo from '../TextLogo/TextLogo.vue';

    export default {
        name: 'black_box_of_header',
        components: {
            btn_link,
            logo,
            humburger,
            top_menu,
            text_logo
        }
    }
</script>

<style lang="scss">
    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .header-box {
        width: 100%;
        @include flexible(space-between, center);
        &__site-logo {
            @include flexible(center, center);
        }
        &__logo {
            padding: 0 12.5px 0 0;
        }
        &__menu-box {
            margin: 0 0 0 auto;
            padding: 0 20px 0 0;
        }
        &__buttons-box {
            display: flex;
        }
        &__btn-small {
            padding: 0 20px 0 0;
        }
    }

    @media screen and (min-width: 992px) {
        .header-box {
            &__humburger-box {
                display: none;
            }
        }
    }

    @media screen and (max-width: 991px) {
        .header-box {
            &__menu,
            &__buttons-box {
                display: none;
            }
        }
    }
</style>