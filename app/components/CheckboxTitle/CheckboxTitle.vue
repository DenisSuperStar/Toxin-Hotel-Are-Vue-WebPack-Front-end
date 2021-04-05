<template lang="pug">
    span(class="checkbox-title") {{titleText}}
</template>

<script>
    export default {
        name: 'checkbox_title',
        props: {
            titleText: String
        }
    }
</script>

<style lang="scss" scoped>

    @import '../../mixinApp.scss';
    @import '../CheckboxTitle/mixinCheckboxTitle.scss';

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .checkbox-title {
        display: block;
        width: 205px;
        height: max-content;
        font-weight: $checkbox_title_weight;
        line-height: $checkbox_title_height;
        font-size: $checkbox_title_size;
        font-family: $app_font;
        color: $checkbox_title_color;
        @include slice();
    }   
</style>