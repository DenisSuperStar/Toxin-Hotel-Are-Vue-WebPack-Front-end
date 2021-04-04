<template lang="pug">
    div(class="range-slider")
        div(class="range-slider__label-box")
            div(class="range-slider__range-label") диапазон
            div(class="range-slider__price") {{begin_range}}
                span(class="range-slider__rub") - {{end_range}}
                span(class="range-slider__rub")
        div(class="range-slider__slider-box")
            div(
                class="range-slider__slider" 
                @click="appearDisplayField"
            )
                input(
                    type="range"
                    class=`
                        range-slider__range
                        range-slider__range--first
                        range-slider__range--current-colored
                    `
                    min="0"
                    max="10000"
                    step="100"
                    v-model="sliderMin"
                )
                input(
                    type="range"
                    class=`
                        range-slider__range
                        range-slider__range--last
                        range-slider__range--current-colored
                    `
                    min="10000"
                    max="20000"
                    step="100"
                    v-model="sliderMax"
                )
</template>

<script>
    export default {
        name: 'range-slider',
        data: () => {
            return {
                begin_range: 6300,
                end_range: 13600,
                show_field: false
            }
        },
        methods: {
           appearDisplayField: function() {
               this.display_field =!this.display_field;
           }
        },
        computed: {
            sliderMin: {
                get: function() {
                    return +(this.begin_range);
                },
                set: function(value) {
                    this.begin_range = +(value);
                }
            },
            sliderMax: {
                get: function() {
                    return +(this.end_range);
                },
                set: function(value) {
                    this.end_range = value;
                    if (this.end_range < 10000) {
                        this.end_range = 10000;
                    }
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../RangeSlider/mixinRangeSlider.scss';

    @mixin range(
        $range-self_width,
        $range-self_height,
        $range-self_background,
        $range-self_default-border-thick,
        $range-self_default_border-style,
        $range-self_default_border-color,
        $range-self_round
    ) {
        width:          $range-self_width;
        height:         $range-self_height;
        background:     $range-self_background;
        border-width:   $range-self_default-border-thick;
        border-style:   $range-self_default_border-style;
        border-color:   $range-self_default_border-color;
        border-radius:  $range-self_round
    }

    @mixin thumb(
        $thumb_width,
        $thumb_height,
        $thumb_default_background,
        $thumb_default_border-thick,
        $thumb_default_border-style,
        $thumb_default-border-color,
        $thumb_round
    ) {
        width:          $thumb_width;
        height:         $thumb_height;
        background:     $thumb_default_background;
        border-width:   $thumb_default_border-thick;
        border-style:   $thumb_default_border-style;
        border-color:   $thumb_default_border-color;
        border-radius:  $thumb_round;
    }

    @mixin rangeCurrent(
        $range_background
    ) {
        background: $range_background;
    }

    @mixin thumbCurrent(
        $thumb_background
    ) {
        background: $thumb_background;
    }


    @media screen and (min-width: 1200px) and (max-width: 1440px) {
        .slider {
            display: flex;
            &__range::-webkit-slider-thumb {
                width: $control_width_less;
                height: $control_height_less;
            }
        }
    }

    .range-slider {
        &__label-box {
            display: flex;
            justify-content: space-between;
        }
        &__range-label,
        &__price {
            font-size: 12px;
            line-height: 15px;
            text-transform: uppercase;
            font-family: $app_font;
        }
        &__range-label {
            font-weight: bold;
            color: #1f2041;
        }
        &__price {
            &, &::after {color: rgba(31, 32, 65, 0.5);}
            &::after {
                content: '\f158';
                font-size: 11px;
                line-height: 15px;
                font-family: $app_font;
            }
        }
        &__slider {
            position: relative;
            width: 100%; 
            /*???*/
            /*На расширении где-то в 1420px указать точные размеры всех элементов по макету*/
            text-align: center;
            padding: 23px 0 0 0;
            cursor: pointer;
        }
        &__range,
        &__range::-webkit-slider-thumb {
            appearance: none;
        }
        &__range {
            position: absolute;
            cursor: pointer;
            &--first {
                left: 0;
            }
            &--last {
                right: 0;
            }
            @include range(
                $range-slider_width,
                $range-slider_height,
                $range-slider_default_background,
                $range-slider_default_border-width,
                $range-slider_default_border-style,
                $range-slider_default_border-color,
                $range-slider_round
            );
            &::-webkit-slider-thumb {
                @include thumb(
                    $slider-thumb_width,
                    $slider-thumb_height,
                    $slider-thumb_default_background,
                    $slider-thumb_default_border-width,
                    $slider-thumb_default_border-style,
                    $slider-thumb_default_border-color,
                    $slider-thumb_round
                );
                cursor: pointer;
                z-index: 2;
            }
            &--current-colored {
                @include rangeCurrent(
                    $range-slider_background
                );
            }
            &--current-colored::-webkit-slider-thumb {
                @include thumbCurrent(
                    $slider-thumb_background
                );
            }
        }
    }
</style>