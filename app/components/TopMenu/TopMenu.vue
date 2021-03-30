<template lang="pug">
    div(class="cm-menu")
        div(class="cm-menu__item" v-for="(item, index) in menu_items" :key="index")
            template(v-if="++index == 2")
                div(class="cm-menu__title")
                    a(
                        class=`
                            cm-menu__link
                            cm-menu__link--tagged
                            cm-menu__link--animated
                            cm-menu__link--slow-motion
                            ` 
                            @click="dropdownToggle($event)"
                    ) {{item}}
                    span(
                        class="cm-menu__icon" 
                        @click="dropdownToggle($event)"
                    )
                div(class=`
                        cm-menu__submenu 
                        cm-menu__submenu--slide-animated
                        cm-menu__submenu--visible
                        cm-menu__submenu--decorated
                        is-slide-down`
                    )
                    ul(class="cm-menu__list cm-menu__list--decorated")
                        template(v-for="name in service_items")
                            li(class=`
                                cm-menu__item 
                                cm-menu__item--colored
                                cm-menu__item--dropped`
                            ) {{name}}
            template(v-else-if="++index == 5")
                div(class="cm-menu__title")
                    a(
                        class=`
                            cm-menu__link 
                            cm-menu__link--tagged
                            cm-menu__link--animated
                            cm-menu__link--slow-motion
                            ` 
                    ) {{item}}
                    span(
                        class="cm-menu__icon" 
                        @click="dropdownToggle($event)"
                    )
                div(class=`
                        cm-menu__submenu 
                        cm-menu__submenu--slide-animated
                        cm-menu__submenu--visible
                        cm-menu__submenu--decorated 
                        is-slide-down`
                    )
                    ul(
                        class=`
                            cm-menu__list 
                            cm-menu__list--decorated
                            `
                    )
                        template(v-for="name in condition_items")
                            li(class=`
                                cm-menu__item 
                                cm-menu__item--colored
                                cm-menu__item--dropped`
                            ) {{name}}
            template(v-else)
                div(class="cm-menu__title")
                    a(
                        href='//google.com' 
                        class=`
                            cm-menu__link
                            cm-menu__link--animated
                            cm-menu__link--slow-motion
                        `
                    ) {{item}}
</template>

<script>
    export default {
        name: 'Menu',
        data: () => {
            return {
                menu_items: [
                    'О нас',
                    'Услуги',
                    'Вакансии',
                    'Новости',
                    'Соглашения'
                ],
                service_items: [
                    'Услуга 1',
                    'Услуга 2',
                    'Услуга 3',
                    'Услуга 4',
                    'Услуга 5'
                ],
                condition_items: [
                    'Соглашение 1',
                    'Соглашение 2',
                    'Соглашение 3',
                    'Соглашение 4',
                    'Соглашение 5'
                ]
            }
        },
        methods: {
            dropdownToggle: function(e) {
                const target = e.target;
                const title = target.parentElement;
                const item = title.parentElement;
                const slide_down = item.querySelector('.is-slide-down');

                if (slide_down.style.maxHeight) {
                    slide_down.style.maxHeight = null;
                } else {
                    slide_down.style.maxHeight = slide_down.scrollHeight + 10 + 'px';
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

@import '../../mixinApp.scss';
@import '../TopMenu/mixinTopMenu.scss';

@mixin slice {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.cm-menu {
    display: flex;
    justify-content: flex-end;
    background: $menu_background;
    &__item {
        position: relative;
    }
    &__title {
        display: flex;
        align-items: center;
        padding: 0 20px 0 0;
    }
    &__link,
    &__link:hover {
        position: relative;
        color: $menu_link_color;
        text-decoration: none;
        font-size: $menu_link_size;
        line-height: $menu_link_height;
        font-family: $app_font;
        cursor: pointer;
        @include slice();
        z-index: 8; /*!!!*/
    }
    &__link {
        &:hover {
            color: $menu_color_link_hovered;
        }
        &::before,
        &::after {
            background: $menu-item_background_hovered;
        }
        &--slow-motion {
            &,
            &:hover {
              transition: color 0.5s ease-in-out;  
            }
            &::before,
            &::after {
               transition: transform 0.5s ease-in-out; 
            }
        }
        &--animated {
            &::before,
            &::after {
                content: '';
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                transform-origin: bottom;
                transform: scaleY(0);
                z-index: -1; /*!!!*/
            }
            &:hover::before,
            &:hover::after {
                transform: scaleY(1);
                transform-origin: top;
                z-index: -2; /*!!!*/
            }
        }
    }
    &__icon::after {
        width: 24px;
        height: max-content;
        display: flex;
        justify-content: center;
        align-items: center;
        content: '\f078';
        font-size: 14px;
        line-height: 20px;
        color: rgba(31, 32, 65, 0.5);
        font-family: 'Font Awesome 5 Pro';
    }
    &__item:last-child &__title {
        padding: 0;
    }
}

@media screen and (max-width: 959px) {
    .cm-menu {
        display: none;
    }
}

/*
    Submenu styles
*/

.cm-menu {
    &__submenu {
        display: block;
        position: absolute;
        right: 0;
        width: 150px;
        background: $submenu_default_background;
        &--slide-animated {
            overflow: hidden;
            max-height: 0;
            transition: max-height 0.5s ease;
        }
        &--decorated {
            border-radius: $submenu_rounding;
        }
        &--visible {
            z-index: 88;
        }
    }
    &__list {
        display: flex;
        flex-flow: column;
        align-items: center;
        width: 100%;
        margin: 0;
        padding: 20px 0;
        list-style: none;
        border-width: $submenu_default_border_width;
        border-style: $submenu_default_border_style;
        border-color: $submenu_default_border_color;
        &--decorated {
            border-radius: $submenu_rounding;
            border-color: $submenu_border_color;
        }
    }
    &__item {
        width: max-content;
        font-size: $submenu_text_size;
        line-height: $submenu_text_height;
        font-family: $app_font;
        background: $submenu_item_default_background;
        color: $submenu_item_default_color;
        &--dropped {
            margin: 0 0 20px;
        }
        &:last-child {
            margin: 0;
        }
        &--colored {
            color: $submenu_item_color;
        }
    }
}
</style>