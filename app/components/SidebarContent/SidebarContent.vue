<template lang="pug">
    div(class="sidebar-box")
        div(class="sidebar-box__subheader-box sidebar-box__subheader-box--large")
            subheader(:subheader-text="title_date_ranges")
        div(class="sidebar-box__dropdownbox")
            select_simple(:options="date_ranges" :placeholder="start_date" master="first")
        div(class="sidebar-box__subheader-box sidebar-box__subheader-box--extra-small")
            subheader(:subheader-text="title_count_arrivals")
        div(class="sidebar-box__dropdownbox")
           select_simple(:options="count_arrivals" :placeholder="start_count") 
        div(class="sidebar-box__title-range-box") 
            //div(class="title-range") диапазон
            //div(class="title-range-price") 5 000<span class="title-range-price__rub"></span> - 10 000<span class="title-range-price__rub"></span>
        div(class="sidebar-box__range-slider")
            range_slider
        div(class="sidebar-box__checkboxes-block")
            div(class="sidebar-box__rules-block")
                div(class="sidebar-box__subheader-box sidebar-box__subheader-box--medium-simple")
                    subheader(:subheader-text="title_block_simple_checkboxes")
                template(v-for="(label, index) in labels")
                    div(class="sidebar-box__checkbox")
                        checkbox(:check-mark="label.checked")
                        template(v-if="index==2")
                            label_checkbox(
                                :label-text="label.text"
                                uniq-class="label-checkbox--uniq"
                            )
                        template(v-else)
                            label_checkbox(:label-text="label.text")
            div(class="sidebar-box__has-block")
                div(class="sidebar-box__subheader-box sidebar-box__subheader-box--medium-complex")
                    subheader(:subheader-text="title_block_complex_checkboxes")
                template(v-for="(string, index) in layer_text")
                    div(class="sidebar-box__grid-text")
                        checkbox
                        div(class="sidebar-box__multiple-text")
                            div(class="sidebar-box__title-box")
                                checkbox_title(:title-text="string.label")
                            div(class="sidebar-box__text-box")
                                checkbox_text(:self-text="string.text")

        div(class="sidebar-box__subheader-box sidebar-box__subheader-box--middle")
            subheader(:subheader-text="title_living_conditions")
        div(class="sidebar-box__select-counter")
            select_with_counter(:options="counter_resource" :placeholder="preview_resource")
        div(class="sidebar-box__select-score sidebar-box__select-score--free")
            select_score(:options="room_services" :placeholder="service_name")
</template>

<script>
    import checkbox from '../Checkbox/Checkbox.vue';
    import checkbox_title from '../CheckboxTitle/CheckboxTitle.vue';
    import checkbox_text from '../CheckboxText/CheckboxText.vue';
    import range_slider from '../RangeSlider/RangeSlider.vue';
    import subheader from '../Subheader/Subheader.vue';
    import select_simple from '../SelectSimple/SelectSimple.vue';
    import select_with_counter from '../SelectWithCounter/SelectWithCounter.vue';
    import select_score from '../SelectWithCheckBoxes/SelectWithCheckboxes.vue';
    import label_checkbox from '../LabelCheckbox/LabelCheckbox.vue';       

    export default {
        name: 'black_box_sidebar',
        components: {
            checkbox,
            checkbox_title,
            checkbox_text,
            range_slider,
            subheader,
            select_simple,
            select_with_counter,
            select_score,
            label_checkbox
        },
        data: () => {
            return {
                title_block_simple_checkboxes: 'Правила дома',
                title_block_complex_checkboxes: 'Доступность',
                title_date_ranges: 'Даты пребывания в отеле',
                title_count_arrivals: 'Гости',
                title_living_conditions: 'Удобства номера',
                start_date: '9 авг - 13 авг',
                start_count: '3 гостя, 1 младенец',
                date_ranges: [
                    '30 июля - 3 авг',
                    '4 авг - 8 авг',
                    '9 авг - 13 авг',
                    '14 авг - 18 авг',
                    '19 авг - 23 авг',
                    '24 авг - 28 авг',
                    '29 авг - 2 сен',
                ],
                count_arrivals: [
                    '1 гость',
                    '2 гостя',
                    '3 гостя, пара с 1 ребенком',
                    '3 гостя, 1 младенец',
                    '4 гостя, пара с 2 детьми'
                ],
                labels: [
                    {
                        checked: 'checked', 
                        text: 'Можно курить'
                    },
                    {
                        checked: 'checked', 
                        text: 'Можно с питомцами',
                    },
                    {
                        checked: 'checked', 
                        text: 'Можно пригласить гостей (до 10 человек)'
                    }
                ],
                layer_text: [
                    {
                        label: 'Широкий коридор', 
                        text: 'Ширина коридоров в номере не менее 91 см.'
                    },
                    {
                        label: 'Помощник для инвалидов', 
                        text: `
                            На первом этаже вас встретит специалист
                            и проводит до номера
                            `
                    },
                ],
                counter_resource: [
                    {name: 'спальни', count: 2},
                    {name: 'кровати', count: 2},
                    {name: 'ванные комнаты', count: 0}
                ],
                preview_resource: '',
                room_services: [
                    {
                        checked: '', 
                        text: 'Завтрак'
                    },
                    {
                        checked: 'checked',
                        text: 'Письменный стол'
                    },
                    {
                        checked: 'checked', 
                        text: 'Стул для кормления'
                    },
                    {
                        checked: 'checked', 
                        text: 'Кроватка'
                    },
                    {
                        checked: '', 
                        text: 'Телевизор'
                    },
                    {
                        checked: '', 
                        text: 'Шампунь'
                    },
                    {
                        checked: '', 
                        text: 'Телевизор'
                    },
                    {
                        checked: '', 
                        text: 'Шампунь'
                    }
                ],
                service_name: 'Дополнительные удобства'
            }
        },
        created: function() {
            /*
                Не используются функции
                slice, splice, substr.
                Если позиция символа в строке изменится,
                тогда нужно будет снова ее вычислять
            */
            let start_value = 0;
            let end_value = this.counter_resource.length - 1;
            let middle_value = Math.floor((end_value - start_value) / 2);

            let total = '';
            let target = '';
            let last = '';
            let count = 0;

            for (const value of this.counter_resource) {
                total += value.count + ' ' + value.name + ', ';
                if ((count > start_value) && (count < end_value)) {
                    target = total;
                    total = '';
                } else if (count > middle_value) {
                    last = value.count + ' ' + value.name;
                }
                count++;
            }

            this.preview_resource = target + last;
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinGlobal.scss';

    .sidebar-box {
        padding: 0 59px 0 140px;
    }

    @media screen and (min-width: 1400px) and (max-width: 1470px) {
        .sidebar-box {
            padding: 0;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1399px) {
        .sidebar-box {
            padding: 0 0 0 30px;
        }
    }

    @media screen and (min-width: 960px) and (max-width: 1199px) {
        .sidebar-box {
            padding: 0 calc(59px / 2.4) 0 30px;
        }
    }

    @media screen and (min-width: 768px) and (max-width: 959px) {
        .sidebar-box {
            padding: 0 30px;
        }
    }

    @media screen and (max-width: 767px) {
        .sidebar-box {
            padding: 0 50px;
        }
    }

    .sidebar-box {
        &__subheader-box {
            &--large {
               padding: 30px 0 5px 0; 
            }
            &--extra-small {
                padding: 20.44px 0 4.56px 0;
            }
            &--medium-simple {
                padding: 30px 0 16.56px 0;
            }
            &--medium-complex {
                padding: 30.88px 0 16px 0;
            }
            &--middle {
                padding: 30px 0 4.56px 0;
            }
        }
        &__title-range-box {
            @include flexible(space-between, center);
            width: 100%;
            padding: 30.44px 0 0 0;
        }
        &__grid-text {
            padding: 0 0 10px 0;
        }
        &__checkbox {
            padding: 0 0 10.56px 0;
        }
        &__checkbox,
        &__grid-text {
            display: flex;
            &:last-child {
                padding: 0;
            }
        }
        &__title-box {
            padding: 0 0 5px;
        }
        &__select-score {
            &--free {
                margin: 16px 0 0 0;
            }
        }
    }

    .title-range {
        font-weight: bold;
        font-size: 12px;
        line-height: 15px;
        text-transform: uppercase;
        color: #1f2041;
        font-family: 'Montserrat', sans-serif;
    }

    .title-range-price {
        font-size: 12px;
        line-height: 15px;
        text-transform: uppercase;
        color: rgba(31, 32, 65, 0.5);
        font-family: 'Montserrat', sans-serif;
    }

    .title-range-price__rub::after {
        content: '\f158';
        font-family: 'Font Awesome 5 Pro';
        color: rgba(31, 32, 65, 0.5);
        font-size: 11px;
        line-height: 15px;
    }
</style>