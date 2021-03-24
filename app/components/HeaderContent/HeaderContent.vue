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
            div(class="header-box__sign-in")
                just_btn(
                        selected-btn-class="btn--signed-in" 
                        added-uniq-id="short" 
                        btn-text="Войти"
                )
            div(class="header-box__sign-up")
                just_btn(
                        selected-btn-class="btn--signed-up" 
                        added-uniq-id="long" 
                        btn-text="Зарегистрироваться"
                )
                
</template>

<script>
    import just_btn from '../JustBtn/JustBtn.vue';
    import logo from '../Logo/Logo.vue';
    import humburger from '../HumburgerMenu/HumburgerMenu.vue'
    import top_menu from '../TopMenu/TopMenu.vue';
    import text_logo from '../TextLogo/TextLogo.vue';

    export default {
        name: 'black_box_of_header',
        components: {
            just_btn,
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
        &__sign-in {
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
            &__menu-box {
                margin: 0;
                padding: 0;
            }
            &__buttons-box {
                display: none;
            }
        }
    }
</style>