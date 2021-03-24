<template lang="pug">
    div(class="range-slider" @click="apperField")
        input(
            type="range" 
            class=`
                range-slider__range 
                current-color
                range-slider__range--colored` 
            min="5000" 
            max="10000" 
            step="100" 
            v-model="sliderMin"
        )
        input(
            type="number" 
            class=`
                range-slider__number 
                range-slider__number--colored 
                range-slider__number--transparented` 
            min="5000" 
            max="10000" 
            step="100" 
            v-model="sliderMin" 
            v-show="show_field"
        )
        input(
            type="range" 
            class=`
                range-slider__range
                current-color 
                range-slider__range--colored` 
            min="5000" 
            max="10000" 
            step="100"  
            v-model="sliderMax"
        )
        input(
            type="number" 
            class=`
                range-slider__number 
                range-slider__number--colored 
                range-slider__number--transparented` 
            min="5000" 
            max="10000" 
            step="100" 
            v-model="sliderMax" v-show="show_field"
        )
</template>

<script>
    export default {
        name: 'range-slider',
        data: () => {
            return {
                begin_range: 6500,
                end_range: 8500,
                show_field: false
            }
        },
        methods: {
           apperField: function() {
               this.show_field =!this.show_field;
           }
        },
        computed: {
            sliderMin: {
                get: function() {
                    const number = +(this.begin_range);
                    return number;
                },
                set: function(number) {
                    const value = +(number);
                    if (value > this.end_range) {
                        this.end_range = value;
                    }
                    this.begin_range = value;
                }
            },
            sliderMax: {
                get: function() {
                    const number = +(this.end_range);
                    return number;
                },
                set: function(number) {
                    const value = +(number);
                    if (value < this.begin_range) {
                        this.begin_range = value;
                    }
                    this.end_range = value;
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

    @import '../RangeSlider/mixinRangeSlider.scss';

    .range-colored {
        background: $control_background;
    }

    .range-slider {
        position: relative;
        width: 100%; /*На расширении где-то в 1420px указать точные размеры всех элементов по макету*/
        text-align: center;
        height: max-content;
        padding: 23px 0 0 0;
        cursor: pointer;
        &__range {
            position: absolute;
            left: 0;
            bottom: 0;
            appearance: none;
            width: 100%;
            height: $range-slider_height;
            border-radius: $range-slider_rounded_corner;
            background: $range-slider_default_background;
            border: $range-slider_default_border;
        }
        &__range::-webkit-slider-thumb {
            z-index: 2;
            position: relative;
            appearance: none;
            width: $control_width;
            height: $control_height;

            border-width: $control_default_border;
            border-style: $control_default_border;
            border-color: $control_default_border;

            border-radius: $control_rounding;
            background: $control_default_background;
            cursor: pointer;
        }
        &__range {
            /*
                range-slider style
            */
            &--colored.current-color {
                @extend .range-colored;
            }
            /*
                control of range-slider styles
            */
            &--colored.current-color::-webkit-slider-thumb {
                @extend .range-colored;
            }
        }
        &__number {
            width: $field_width;
            text-align: center;
            color: $field_default_color;
            background: $field_default_background;
            border-width: $field_default_border-thick;
            border-style: $field_default_border-style;
            border-color: $field_default_border-color;
            border-radius: $field_rounding;
            margin: 0 0 23.44px 0;
            font: 14px / 24px 'Montserrat', sans-serif;
            &:last-child {
                margin: 0 0 23.44px 103.44px;
            }
            &--colored {
                border-width: $field_border-thick;
                border-style: $field_border-style;
                border-color: $field_border-color;
                color: $field_color;
                background: $field_background;
            }
            &--transparented {
                opacity: $field_opacity;
            }
            &::-webkit-outer-spin-button,
            &::-webkit-inner-spin-button {
                appearance: none;
            }
            /*
                If out of range then input fields view with color danger
            */
            &:invalid,
            &:out-of-range {
                /*border: 2px solid #ff6347;*/
                border-width: $field_invalid_border-thick;
                border-style: $field_invalid_border-style;
                border-color: $field_invalid_border-color;
            }
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1440px) {
        .range-slider {
            display: flex;
            &__range::-webkit-slider-thumb {
                width: $control_width_less;
                height: $control_height_less;
            }
        }
    }
</style>