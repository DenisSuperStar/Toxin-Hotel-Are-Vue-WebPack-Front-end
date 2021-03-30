<template lang="pug">
    span(class="checkbox-text") {{selfText}}
</template>

<script>
    export default {
        name: 'checkbox_text',
        props: {
            selfText: String
        }
    }
</script>

<style lang="scss" scoped>
    
    @import '../../mixinApp.scss';
    @import '../CheckboxText/mixinCheckboxText.scss';

    @mixin valid {
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .checkbox-text {
        display: block;
        width: $checkbox_text-block_width;
        height: max-content;
        font-size: $checkbox_text_size;
        line-height: $checkbox_text_height;
        font-family: $app_font;
        color: $checkbox_text_color;
        @include valid();
    }
</style>