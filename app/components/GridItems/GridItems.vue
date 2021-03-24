<template lang="pug">
    div(class="grid-items")
        div(class="grid-items__title")
            div Title
        div(class="grid-items__items")
            div(class="grid-items__item")
                div(class="grid-items__box-item" v-for="item in room_info" :key="item.id")
                    template(v-if="((item.id >= 1) && (item.id <= 3))")
                        card(
                            :number="item.number"
                            :number-type="item.number_type"
                            :price="item.price"
                            :period="item.period"
                            :count-review="item.count_review"
                            :room-id="item.room_id"
                            :count-active-stars="item.active_stars"
                            :class="{'is-last-card': item.id == 3}"
                        )
            div(class="grid-items__item")
                div(class="grid-items__box-item" v-for="item in room_info" :key="item.id")
                    template(v-if="((item.id >= 4) && (item.id <= 6))")
                        card(
                            :number="item.number"
                            :number-type="item.number_type"
                            :price="item.price"
                            :period="item.period"
                            :count-review="item.count_review"
                            :room-id="item.room_id"
                            :count-active-stars="item.active_stars"
                            :class="{'is-last-card': item.id == 6}"
                        )
                        
            div(class="grid-items__item")
                div(class="grid-items__box-item" v-for="item in room_info" :key="item.id")
                    template(v-if="((item.id >= 7) && (item.id <= 9))")
                        card(
                            :number="item.number"
                            :number-type="item.number_type"
                            :price="item.price"
                            :period="item.period"
                            :count-review="item.count_review"
                            :room-id="item.room_id"
                            :count-active-stars="item.active_stars"
                            :class="{'is-last-card': item.id == 9}"
                        )
            div(class="grid-items__item")
                div(class="grid-items__box-item" v-for="item in room_info" :key="item.id")
                    template(v-if="((item.id >= 10) && (item.id <= count_groups))")
                        card(
                            :number="item.number"
                            :number-type="item.number_type"
                            :price="item.price"
                            :period="item.period"
                            :count-review="item.count_review"
                            :room-id="item.room_id"
                            :count-active-stars="item.active_stars"
                            :class="{'is-last-card': item.id == count_groups}"
                        )
</template>

<script> 
    import card from '../Card/Card.vue';

    export default {
        name: 'grid_items',
        components: {
            card
        },
        data: () => {
            return {
                review_text: '',
                count_groups: 12,
                room_info: [
                    {
                        id: 1,
                        number: 888,
                        number_type: 'люкс',
                        price: 9900,
                        period: 'в сутки',
                        count_review: 145,
                        room_id: 1,
                        active_stars: 5
                    },
                    {
                        id: 2,
                        number: 840,
                        number_type: '',
                        price: 9900,
                        period: 'в сутки',
                        count_review: 65,
                        room_id: 2,
                        active_stars: 4
                    },
                    {
                        id: 3,
                        number: 980,
                        number_type: 'люкс',
                        price: 8500,
                        period: 'в сутки',
                        count_review: 35,
                        room_id: 3,
                        active_stars: 3
                    },
                    {
                        id: 4,
                        number: 856,
                        number_type: '',
                        price: 7300,
                        period: 'в сутки',
                        count_review: 19,
                        room_id: 4,
                        active_stars: 5
                    },
                    {
                        id: 5,
                        number: 740,
                        number_type: '',
                        price: 6000,
                        period: 'в сутки',
                        count_review: 44,
                        room_id: 5,
                        active_stars: 4
                    },
                    {
                        id: 6,
                        number: 982,
                        number_type: '',
                        price: 5800,
                        period: 'в сутки',
                        count_review: 56,
                        room_id: 6,
                        active_stars: 3
                    },
                    {
                        id: 7,
                        number: 678,
                        number_type: '',
                        price: 5500,
                        period: 'в сутки',
                        count_review: 45,
                        room_id: 7,
                        active_stars: 5
                    },
                    {
                        id: 8,
                        number: 450,
                        number_type: '',
                        price: 5300,
                        period: 'в сутки',
                        count_review: 39,
                        room_id: 8,
                        active_stars: 4
                    },
                    {
                        id: 9,
                        number: 350,
                        number_type: '',
                        price: 5000,
                        period: 'в сутки',
                        count_review: 77,
                        room_id: 9,
                        active_stars: 3
                    },
                    {
                        id: 10,
                        number: 666,
                        number_type: '',
                        price: 5000,
                        period: 'в сутки',
                        count_review: 25,
                        room_id: 10,
                        active_stars: 5
                    },
                    {
                        id: 11,
                        number: 444,
                        number_type: '',
                        price: 5000,
                        period: 'в сутки',
                        count_review: 15,
                        room_id: 11,
                        active_stars: 4
                    },
                    {
                        id: 12,
                        number: 352,
                        number_type: '',
                        price: 5000,
                        period: 'в сутки',
                        count_review: 55,
                        room_id: 12,
                        active_stars: 3
                    }
                ]
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

    .grid-items {
        width: 100%;
        margin: 0 140px 0 0;
        max-width: 835px;
    }

    @media screen and (min-width: 992px) and (max-width: 1199px) {
        .grid-items {
            margin: 0 30px 0 0;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1440px) {
        .grid-items {
            margin: 0 auto 0 0;
        }
    }

    .grid-items {
        &__title {
            margin: 0 250px 0 0;
            padding: 0 0 21px;
        }
    }

    @media screen and (max-width: 1200px) {
        .grid-items {
            &__title {
                margin: 0;
                padding: 21px 0;
            }
        }
    }

    .grid-items {
        &__items {
            margin: 0 0 12px;
        }
    }

    .grid-items {
        &__item {
            width: 100%;
            @include flexible(center, center);
            flex-flow: row;
            margin: 0 0 18px;
            &:last-child {
                margin: 0;
            }
        }
    }

    @media screen and (max-width: 1140px) {
        .grid-items {
            &__item {
                display: flex;
                flex-flow: column;
                margin: 0;
            }
            &__item > &__box-item {
                @include flexible(center, center);
                margin: 0 0 12px 0;
                &:last-child {
                    margin: 0;
                }
            }
        }
    }

    /*@media screen and (min-width: 961px) and (max-width: 1140px) {
        .grid-items {
            &__box-item {
                width: 32%;
            }
        }
    }

    @media screen and (max-width: 960px) {
        .grid-items {
            &__box-item {
                width: 100%;
            }
        }
    }*/
</style>