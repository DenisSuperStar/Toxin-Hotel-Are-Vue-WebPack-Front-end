<template lang="pug">
    form(class="form-sending")
        label(class="form-sending__input-box")
            input(
                type="email"
                class=`
                    form-sending__data
                    form-sending__data--decorated
                    form-sending__data--single
                `
                name="email"
                size="20"
                pattern=".+@google.com"
                required
            )
            label(class="form-sending__label-of-input form-sending__label-of-input--animated") Email
</template>

<script>
    export default {
        name: 'form_sending'
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../FormSending/mixinFormSending.scss';

    .form-sending {
        &__input-box {
            position: relative;
            display: flex;
            height: $input_height;
            margin: 20px 0 0 0;
        }
        &__data {
            position: absolute;
            top: 0;
            bottom: 0;
            background: $input_default_background;

            border-width: none;
            border-style: none;
            border-color: none;

            font-size: $input_default_size_text;
            line-height: $input_default_height_text;
            font-family: $app_font;
            cursor: pointer;
            &--decorated {
                border-width: $input_border-width;
                border-style: $input_border-style;
                border-color: $input_border-color;

                border-radius: $input_round;
            }
            &--single {
                width: $input_width;
                padding: 12px 0 12px 15px;
            }
        }
        &__data:focus + &__label-of-input {
            position: absolute;
            padding: 13px 0 0 15px;
            color: $input_placeholder_color;
            &--animated {
                transform: translateY(-25px);
                font-size: 12px;
            }
        }
        &__data + &__label-of-input {
            line-height: $input_default_height_text;
            color: $input_placeholder_color;
            padding: 13px 0 13px 15px;
            pointer-events: none;
            &--animated {
                transform: translateY(0);
                transition: all 0.5s ease;
            }
        }
    }

    @media screen and (max-width: 959px) {
        .form-sending {
            &__data {
                width: 100%;
                font-size: 16px;
            }
        }
    }
</style>