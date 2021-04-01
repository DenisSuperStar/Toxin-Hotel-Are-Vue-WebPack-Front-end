<template lang="pug">
    div(class="navigation")
        div(class="navigation__root-box")
            div(class="navigation__logo-box")
                logo
                div(class="navigation__label-box")
                    text_logo
            div(class="navigation__description-box")
                description_logo_nav(:nav-description="nav_description")
        div(class="navigation__list-box")
            nav_list(:data-list="nav")
        div(class="navigation__list-box")
            nav_list(:data-list="about")
        div(class="navigation__list-box")
            nav_list(:data-list="contacts")
        div(class="navigation__list-box")
            sending_list
</template>

<script>
    import description_logo_nav from '../DescriptionLogoNav/DescriptionLogoNav.vue';
    import logo from '../Logo/Logo.vue';
    import nav_list from '../NavList/NavList.vue';
    import text_logo from '../TextLogo/TextLogo.vue';
    import sending_list from '../SendingList/SendingList.vue';

    export default {
        name: 'navigation',
        components: {
            description_logo_nav,
            logo,
            nav_list,
            text_logo,
            sending_list
        },
        data: () => {
            return {
                nav_description: 'Бронирование номеров в лучшем отеле 2019 года по версии ассоциации "Отдельные взгляды"',
                nav: [
                    'Навигация',
                    'О нас',
                    'Новости',
                    'Служба поддержки',
                    'Услуги'
                ],
                about: [
                    'О нас',
                    'О сервисе',
                    'Наша команда',
                    'Вакансии',
                    'Инвесторы'
                ],
                contacts: [
                    'Служба поддержки',
                    'Соглашения',
                    'Сообщества',
                    'Связь с нами',
                    ' '
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../Navigation/mixinFooterNav.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    .navigation {
        width: $footer-nav_width;
        @include flexible(space-between, flex-start);
        padding: 104px 140px 100px 140px;
        box-shadow: 0 1px 0 $footer-nav_shadow-color;
        &__logo-box {
            display: flex;
            align-items: center;
        }
        &__label-box {
            padding: 0 0 0 12.5px;
        }
        &__description-box {
            padding: 20px 0 0 0;
        }
    }

    @media screen and (max-width: 720px) {
        .navigation {
            display: flex;
            flex-flow: column;
            padding: 104px 0 25px 50px;
        }
    }

     @media screen and (min-width: 721px) and (max-width: 959px) {
        .navigation {
            display: flex;
            flex-flow: column;
            align-items: center;
        }
    }

    @media screen and (min-width: 960px) and (max-width: 1199px) {
        .navigation {
            display: flex;
            justify-content: space-between;
            padding: 104px 30px 100px;
        }
    }

    @media screen and (max-width: 959px) {
        .navigation {
            &__description-box {
                padding: 20px 0;
            }
        }
    }
</style>