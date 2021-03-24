<template lang="pug">
    div(class="humburger-menu")
        div(
            class=`
                humburger-menu__btn
                humburger-menu__btn--bright
                humburger-menu__btn--rounded
                humburger-menu__btn--slowled`
                @click.self="toggleShow"
        )
            div(class="humburger-menu__strike")
        div(class="humburger-menu__dropdown" :class="{shown: show}" v-show="show")
            div(class="humburger-menu__item")
                a(class="humburger-menu__link") О нас
            div(class="humburger-menu__item" @click="toggleSubmenu($event)")
                span(class="humburger-menu__link") Услуги
                div(class="humburger-menu__submenu")
                    ul(class="humburger-menu__submenu-list")
                        li(class="humburger-menu__submenu-item") Услуга 1
                        li(class="humburger-menu__submenu-item") Услуга 2
                        li(class="humburger-menu__submenu-item") Услуга 3
                        li(class="humburger-menu__submenu-item") Услуга 4
            div(class="humburger-menu__item")
                a(class="humburger-menu__link") Вакансии
            div(class="humburger-menu__item")
                a(class="humburger-menu__link") Новости
            div(class="humburger-menu__item" @click="toggleSubmenu($event)")
                span(class="humburger-menu__link") Соглашения
                div(class="humburger-menu__submenu")
                    ul(class="humburger-menu__submenu-list")
                        li(class="humburger-menu__submenu-item") Соглашение 1
                        li(class="humburger-menu__submenu-item") Соглашение 2
                        li(class="humburger-menu__submenu-item") Соглашение 3
                        li(class="humburger-menu__submenu-item") Соглашение 4
            div(class="humburger-menu__item")
                div(class="humburger-menu__button-box")
                    button(class="btn btn--mobile btn--signed-in") Войти
            div(class="humburger-menu__item")
                div(class="humburger-menu__button-box")
                    button(class="btn btn--mobile btn--signed-up") Зарегистрироваться
</template>

<script>
    export default {
        name: 'HumburgerMenu',
        data: () => {
            return {
                show: false
            }
        },
        methods: {
            toggleShow: function() {
                this.show =!this.show;
            },
            toggleSubmenu: function(e) {
                const self = e.target;
                self.classList.toggle('current');
            }
        }
    }
</script>

<style lang="scss" scoped>

    @import '../HumburgerMenu/HumburgerMenu.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .humburger-menu {
        &__btn {
            position: relative;
            @include flexible(center, center);
            width: $humburger-menu_width;
            height: $humburger-menu_height;
            background: $humburger-menu_default_background;
            border-width: $humburger-menu_default_border_thick;
            border-style: $humburger-menu_default_border_style;
            border-color: $humburger-menu_default_border_color;
            cursor: pointer;
            &--bright {
                border-width: $humburger-menu_border_thick;
                border-style: $humburger-menu_border_style;
                border-color: $humburger-menu_border_color;
            }
            &--rounded {
                border-radius: $humburger-menu_rounded;
            }
            &::before {
                margin: -15px 0 0 0;
            }
            &::after {
                margin: 15px 0 0 0;
            }
            &::before,
            &:hover::before,
            &::after,
            &:hover::after {
                position: absolute;
                display: block;
                content: "";
                width: $humburger-menu-side-line_width;
                height: $humburger-menu-side-line_height;
            }
            &--slowled {
                transition: all 0.75s ease-in-out;
                &::after {
                    transition: all 1s ease;
                }
            }
        }
        &__btn--bright &__strike {
            position: relative;
            display: block;
            width: $humburger-menu-central-line_width;
            height: $humburger-menu-central-line_height;
        }
        &__btn::before,
        &__btn:hover::before,
        &__btn::after,
        &__btn:hover::after,
        &__btn &__strike {
            background: $humburger-menu-line_default_background;
        }
        &__btn--bright::before,
        &__btn--bright:hover::before,
        &__btn--bright::after,
        &__btn--bright:hover::after,
        &__btn--bright &__strike {
            background: $humburger-menu-line_background;
        }
        &__dropdown {
            position: absolute;
            display: flex;
            width: 250px;
            flex-flow: column;
            right: 0;
            background: #fff;
            z-index: 999;
            margin: 15px 2px 0 0;
        }
        &__item {
            position: relative;
            @include flexible(center, center);
            flex-flow: column;
            border-top-width: 2px;
            border-top-style: solid;
            border-top-color: #8ba4f9;
            height: 80px;
        }
        &__link {
            font-size: 16px;
            font-family: 'Montserrat', sans-serif;
            text-transform: uppercase;
            color: rgba(31, 32, 65, 0.5);
            cursor: pointer;
        }
        &__submenu {
            position: absolute;
            width: 100%;
            margin: 240px 0 0 0;
            z-index: 999;
            /*
                Glide open submenu
            */
            overflow: hidden;
            max-height: 0;
        }
        /*
            Glide open submenu
        */
        &__item.current &__submenu {
            max-height: 380px;
        }
        &__submenu-item {
            @include flexible(center, center);
            background: #fff;
            color: rgba(31, 32, 65, 0.5);
            padding: 10px;
            font-size: 16px;
            font-family: 'Montserrat', sans-serif;
        }
    }
</style>