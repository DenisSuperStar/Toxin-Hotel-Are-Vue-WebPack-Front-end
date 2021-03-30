<template lang="pug">
    div(class="card-rotating card-rotating--main")
        div(
            class=`
                card-rotating__card-box 
                card-rotating__card-box--animated 
                card-rotating__card-box--slow-motion
                ` 
                :class="{'is-turn-card': rotate}"
            )
            div(class="card-rotating__self-card card-rotating__self-card--front-side")
                div(class="card-rotating__carousel")
                    div(class="card-rotating__list-item")
                        template(v-for="(page, index) in pages")
                            div(
                                    class="card-rotating__item" 
                                    v-if="roomId == page.album_id" 
                                    :class="{'is-active-item': page.switch_id == active}"
                                )
                                div(
                                    class=`
                                        card-rotating__img-box 
                                        card-rotating__img-box--reshaped`
                                )
                                    img(
                                        :src="page.url" 
                                        class=`
                                            card-rotating__img 
                                            card-rotating__img--reshaped`
                                        @click="turn"
                                    )
                    ul(
                        class=`
                            card-rotating__tab-list 
                            card-rotating__tab-list--relocatable
                            card-rotating__tab-list--free-around
                            `
                        )
                        template(v-for="(dot, index) in slides")
                            li(
                                class=`
                                    card-rotating__tab
                                    card-rotating__tab--repainted
                                    card-rotating__tab--modified-form
                                    card-rotating__tab--free-around
                                    `
                                    :class="{'is-active-tab': ++index == active}"
                                    @click="jump(dot)"

                            )
                div(
                    class=`
                        card-rotating__card-body 
                        card-rotating__card-body--relocatable
                        `
                    )
                    div(class="card-rotating__card-title")
                        div(class="card-rotating__number-box")
                            div(class="card-rotating__number-box")
                                div(class="card-rotating__prefix") №
                                div(class="card-rotating__number") {{number}}
                            div(class="card-rotating__number-type") {{numberType}}
                        div(class="card-rotating__price-box")
                            div(class="card-rotating__price") {{price}}
                            div(class="card-rotating__period-box")
                                span(class="card-rotating__period") {{period}}
                    div(class="card-rotating__hr-box")
                        hl
                    div(class="card-rotating__user-zone")
                        div(class="card-rotating__rating-box")
                            div(class="card-rotating__star-rating")
                                template(v-for="item in count_stars")
                                    div(class="card-rotating__star")
                                        a(
                                            class="card-rotating__star-link"
                                            :class="{'is-active-star': item <= data_active}"
                                            @click="set(item)"
                                        )
                        div(class="card-rotating__review-box")
                            span(class="card-rotating__count-review") {{countReview}}
                            span(class="card-rotating__review-text") {{reviewText}}
            div(
                class=`
                    card-rotating__background-side 
                    card-rotating__background-side--relocatable
                    card-rotating__background-side--rotated-animated
                    ` 
                    @click="turn"
                )
                span(
                    class=`
                        card-rotating__content-background 
                        card-rotating__content-background--dynamic-stretching`
                    ) {{content_background}}
                div(class="card-rotating__redirect-button-box")
                    redirect_link
</template>

<script>
    import hl from '../Hr/Hr.vue';
    import redirect_link from '../RedirectButton/RedirectButton.vue';

    export default {
        name: 'Card',
        components: {
            hl,
            redirect_link
        },
        data: () => {
            return {
                star: 0,
                content_background: `
                    Взору гостей открывается огромное сооружение,
                    венчающий комплекс из 3-х небоскребов
                `,
                count_stars: 5,
                slides: 4,
                active: 1,
                count_active: 1,
                rotate: false,
                data_active: 0,
                pages: [
                    {
                        id: 1,
                        album_id: 1,
                        url: 'https://via.placeholder.com/600/92c952',
                        switch_id: 1
                    },
                    {
                        id: 2,
                        album_id: 1,
                        url: 'https://via.placeholder.com/600/771796',
                        switch_id: 2
                    },
                    {
                        id: 3,
                        album_id: 1,
                        url: 'https://via.placeholder.com/600/24f355',
                        switch_id: 3
                    },
                    {
                        id: 4,
                        album_id: 1,
                        url: 'https://via.placeholder.com/600/d32776',
                        switch_id: 4
                    },
                    {
                        id: 5,
                        album_id: 2,
                        url: 'https://via.placeholder.com/600/f66b97',
                        switch_id: 1
                    },
                    {
                        id: 6,
                        album_id: 2,
                        url: 'https://via.placeholder.com/600/56a8c2',
                        switch_id: 2
                    },
                    {
                        id: 7,
                        album_id: 2,
                        url: 'https://via.placeholder.com/600/b0f7cc',
                        switch_id: 3
                    },
                    {
                        id: 8,
                        album_id: 2,
                        url: 'https://via.placeholder.com/600/54176f',
                        switch_id: 4
                    },
                    {
                        id: 9,
                        album_id: 3,
                        url: 'https://via.placeholder.com/600/51aa97',
                        switch_id: 1
                    },
                    {
                        id: 10,
                        album_id: 3,
                        url: 'https://via.placeholder.com/600/810b14',
                        switch_id: 2
                    },
                    {
                        id: 11,
                        album_id: 3,
                        url: 'https://via.placeholder.com/600/1ee8a4',
                        switch_id: 3
                    },
                    {
                        id: 12,
                        album_id: 3,
                        url: 'https://via.placeholder.com/600/66b7d2',
                        switch_id: 4 
                    },
                    {
                        id: 13,
                        album_id: 4,
                        url: 'https://via.placeholder.com/600/197d29',
                        switch_id: 1
                    },
                    {
                        id: 14,
                        album_id: 4,
                        url: 'https://via.placeholder.com/600/61a65',
                        switch_id: 2
                    },
                    {
                        id: 15,
                        album_id: 4,
                        url: 'https://via.placeholder.com/600/f9cee5',
                        switch_id: 3
                    },
                    {
                        id: 16,
                        album_id: 4,
                        url: 'https://via.placeholder.com/600/fdf73e',
                        switch_id: 4
                    },
                    {
                        id: 17,
                        album_id: 5,
                        url: 'https://via.placeholder.com/600/9c184f',
                        switch_id: 1
                    },
                    {
                        id: 18,
                        album_id: 5,
                        url: 'https://via.placeholder.com/600/1fe46f',
                        switch_id: 2
                    },
                    {
                        id: 19,
                        album_id: 5,
                        url: 'https://via.placeholder.com/600/56acb2',
                        switch_id: 3
                    },
                    {
                        id: 20,
                        album_id: 5,
                        url: 'https://via.placeholder.com/600/8985dc',
                        switch_id: 4
                    },
                    {
                        id: 21,
                        album_id: 6,
                        url: 'https://via.placeholder.com/600/5e12c6',
                        switch_id: 1
                    },
                    {
                        id: 22,
                        album_id: 6,
                        url: 'https://via.placeholder.com/600/45601a',
                        switch_id: 2
                    },
                    {
                        id: 23,
                        album_id: 6,
                        url: 'https://via.placeholder.com/600/e924e6',
                        switch_id: 3
                    },
                    {
                        id: 24,
                        album_id: 6,
                        url: 'https://via.placeholder.com/600/8f209a',
                        switch_id: 4
                    },
                    {
                        id: 25,
                        album_id: 7,
                        url: 'https://via.placeholder.com/600/5e3a73',
                        switch_id: 1
                    },
                    {
                        id: 26,
                        album_id: 7,
                        url: 'https://via.placeholder.com/600/474645',
                        switch_id: 2
                    },
                    {
                        id: 27,
                        album_id: 7,
                        url: 'https://via.placeholder.com/600/c984bf',
                        switch_id: 3
                    },
                    {
                        id: 28,
                        album_id: 7,
                        url: 'https://via.placeholder.com/600/392537',
                        switch_id: 4
                    },
                    {
                        id: 29,
                        album_id: 8,
                        url: 'https://via.placeholder.com/600/602b9e',
                        switch_id: 1
                    },
                    {
                        id: 30,
                        album_id: 8,
                        url: 'https://via.placeholder.com/600/372c93',
                        switch_id: 2
                    },
                    {
                        id: 31,
                        album_id: 8,
                        url: 'https://via.placeholder.com/600/a7c272',
                        switch_id: 3
                    },
                    {
                        id: 32,
                        album_id: 8,
                        url: 'https://via.placeholder.com/600/c70a4d',
                        switch_id: 4
                    },
                    {
                        id: 33,
                        album_id: 9,
                        url: 'https://via.placeholder.com/600/501fe1',
                        switch_id: 1
                    },
                    {
                        id: 34,
                        album_id: 9,
                        url: 'https://via.placeholder.com/600/35185e',
                        switch_id: 2
                    },
                    {
                        id: 35,
                        album_id: 9,
                        url: 'https://via.placeholder.com/600/c96cad',
                        switch_id: 3
                    },
                    {
                        id: 36,
                        album_id: 9,
                        url: 'https://via.placeholder.com/600/4d564d',
                        switch_id: 4
                    },
                    {
                        id: 37,
                        album_id: 10,
                        url: 'https://via.placeholder.com/600/ea51da',
                        switch_id: 1
                    },
                    {
                        id: 38,
                        album_id: 10,
                        url: 'https://via.placeholder.com/600/4f5b8d',
                        switch_id: 2
                    },
                    {
                        id: 39,
                        album_id: 10,
                        url: 'https://via.placeholder.com/600/1e71a2',
                        switch_id: 3
                    },
                    {
                        id: 40,
                        album_id: 10,
                        url: 'https://via.placeholder.com/600/3a0b95',
                        switch_id: 4
                    },
                    {
                        id: 41,
                        album_id: 11,
                        url: 'https://via.placeholder.com/600/659403',
                        switch_id: 1
                    },
                    {
                        id: 42,
                        album_id: 11,
                        url: 'https://via.placeholder.com/600/ca50ac',
                        switch_id: 2
                    },
                    {
                        id: 43,
                        album_id: 11,
                        url: 'https://via.placeholder.com/600/6ad437',
                        switch_id: 3
                    },
                    {
                        id: 44,
                        album_id: 11,
                        url: 'https://via.placeholder.com/600/29fe9f',
                        switch_id: 4
                    },
                    {
                        id: 45,
                        album_id: 12,
                        url: 'https://via.placeholder.com/600/c4084a',
                        switch_id: 1
                    },
                    {
                        id: 46,
                        album_id: 12,
                        url: 'https://via.placeholder.com/600/e9b68',
                        switch_id: 2
                    },
                    {
                        id: 47,
                        album_id: 12,
                        url: 'https://via.placeholder.com/600/b4412f',
                        switch_id: 3
                    },
                    {
                        id: 48,
                        album_id: 12,
                        url: 'https://via.placeholder.com/600/68e0a8',
                        switch_id: 4
                    }
                ]
            }
        },
        methods: {
            jump: function(page) {
                this.active = page;
            },
            turn: function() {
                this.rotate =! this.rotate;
            },
            set: function(value) {
                this.data_active = value;
            }
        },
        created: function() {
            this.data_active = this.countActiveStars; 
        },
        props: {
            number: {
                type: Number,
                default: 0
            },
            numberType: {
                type: String,
                default: ''
            },
            price: {
                type: Number,
                default: 0
            },
            period: {
                type: String,
                default: ''
            },
            countReview: {
                type: Number,
                default: 0
            },
            reviewText: {
                type: String,
                default: 'Отзывов'
            },
            roomId: {
                type: Number,
                default: 1
            },
            countActiveStars: {
                type: Number,
                default: 1
            }
        }
    }
</script>

<style lang="scss" scoped>
    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    @media screen and (max-width: 768px) {
        .card-rotating {
            padding: 0;
        }
    }

    .card-rotating {
        padding: 0 12px 0 0;
        &.is-last-card {
            padding: 0;
        }
        &--main {
            perspective: 1000px;
            /*
                the font changed from all text in this block card
            */
            font-family: 'Montserrat', sans-serif;
        }
        &__card-box {
            position: relative;
            &--animated {
                transform-style: preserve-3d;
                transform: rotateY(180deg);  
            }
            &--animated.is-turn-card {
                transform: rotateY(360deg);  
            }
            &--slow-motion {
                transition: transform 1s ease-in-out;
            }
            transition: transform 1s ease-in-out;
        }
        &__card-box
        &__self-card {
            position: relative;
            width: 270px;
            height: 257px;
            background: #fff;
            box-shadow: 0 10px 20px rgba(31, 32, 65, 0.05);
            &--front-side {
                backface-visibility: hidden;
                transform: rotateY(180deg);
            }
        }
        /*
            back side of this card
        */
        &__background-side {
            width: 270px;
            text-align: center;
            background: linear-gradient(180deg, #bc9cff 0, #8ba4f9 100%);
            color: #fff;
            padding: 12px 12px 0 12px;

            &--relocatable {
                position: absolute;
                /*
                    especial way for set the height
                */
                top: 0;
                bottom: 0;
            }
            &--rotated-animated {
                backface-visibility: hidden;
            }
        }
        &__content-background {
            display: flex;
            align-items: center;
            &--dynamic-stretching {
                height: 50%;
            }
        }
        &__carousel {
            position: relative;
            width: 270px;
            height: 151.38px;
            background: transparent;
            /*
                Main moment in slider operation working
            */
            &__item:not(.is-active-item) {
                display: none;
            }
            &__item.is-active-item {
                display: block;
            }
            &__item.is-active-item &__img {
                width: 100%;
                max-height: 151.38px;
            }
            &__tab.is-active-tab {
                background: #fff;
            }
        }
        /*
            Main moment in slider operation working
        */
        &__item:not(.is-active-item) {
            display: none;
        }
        &__item.is-active-item {
            display: block;
        }
        &__item.is-active-item &__img {
            width: 100%;
            max-height: 151.38px;
        }
        /*
            Others slider styles
        */
        &__tab-list {
            display: flex;
            
            &--relocatable {
                position: absolute;
                right: 0;
                bottom: 0;
            }
            &--free-around {
                margin: 0 16.61px 16.61px 0;
            }
        }
        &__tab {
            display: block;
            width: 7.5px;
            height: 7.5px;
            background: #fff;
            cursor: pointer;
            &--free-around {
                margin: 0 8px 0 0;
            }
            &:last-child {
                margin: 0;
            }
            &--repainted {
                border-width: 1px;
                border-style: solid;
                border-color: #fff;

                background: transparent;
                box-shadow: 0 5px 5px rgba(31, 32, 65, 0.3);
            }
            &--modified-form {
                border-radius: 50%;
            }
        }
        &__tab.is-active-tab {
            background: #fff;
        }
        &__card-body {
            width: 100%;
            height: 105.62px;
            padding: 20.12px 18px 19px 20px;
            &--relocatable {
                position: absolute;
                bottom: 0;
            }
        }
        &__card-title,
        &__user-zone {
            display: flex;
            justify-content: space-between;
        }
        &__review-box,
        &__review-text {
            font-size: 14px;
            line-height: 18px;
            color: rgba(31, 32, 65, 0.5);
        }
        &__review-box {
            font-weight: bold;
        }
        &__review-text {
            font-weight: normal;
        }
        &__number-box,
        &__hr-box,
        &__star-rating,
        &__review-box {
            display: flex;
            align-items: center;
        }
        &__price-box {
            width: max-content;
            display: flex;
        }
        &__price {
            @include flexible(center, center);
            width: max-content;
            height: 20px;
            font-weight: bold;
            font-size: 14px;
            line-height: 24px;
            color: rgba(31, 32, 65, 0.5);
            padding: 0 5px 0 0;
        }
        &__prefix {
            font-weight: bold;
            font-size: 12px;
        }
        &__number {
            display: flex;
            align-items: center;
            width: max-content;
            height: 24px;
            font-weight: bold;
            font-size: 17px;
            line-height: 17px;
            color: #1f2041;
            text-transform: uppercase;
            padding: 0 5px 0 5px;
        }
        &__number-type {
            @include flexible(center, center);
            width: 41px;
            height: 15px;
            font-weight: bold;
            font-size: 12px;
            line-height: 15px;
            text-transform: uppercase;
            color: #bc9cff;
        }
        &__period-box {
            width: max-content;
            margin: 0 0 0 auto;
        }
        &__period {
            display: block;
            font-size: 14px;
            line-height: 18px;
            color: rgba(31, 32, 65, 0.5);
        }
        &__count-review {
            padding: 0 5px 0 0;
        }
        &__img-box,
        &__img {
            &--reshaped {
                border-top-left-radius: 4px;
                border-top-right-radius: 4px; 
            }
        }
        &__rating-box {
            padding: 8px 0 0 0;
        }
        /*Gradient rating star*/
        &__star-rating {
            display: flex;
            width: max-content;
            align-items: center;
            overflow: hidden;
        }
        &__star {
            width: auto;
            background: linear-gradient(180deg, #bc9cff 100%, #8ba4f9 100%);
        }
        &__star > &__star-link,
        &__star > &__star-link:hover {
            display: block;
            font-size: 24px;
            line-height: 20px;
            background: #fff;
            mix-blend-mode: screen;
            text-decoration: none;
            cursor: pointer;
        }
        &__star > &__star-link::before {
            content: '\☆'; 
        }
        &__star > &__star-link.is-active-star::before {
            content: '\★';
        }
    }

    @media screen and (max-width: 1140px) {
        .card-rotating {
            padding: 0;
            &,
            &__self-card,
            &__carousel,
            &__background-side {
                width: 260px;
            }
            &__card-box {
                margin: 0 0 12px 0;
            }
            &.is-last-card &__card-box {
                margin: 0 0 12px 0;
            }
        }
    }
</style>