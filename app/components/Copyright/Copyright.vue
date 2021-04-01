<template lang="pug">
    span(class="copyright") Copyright © 2018 Toxin отель. Все права защищены
</template>

<script>
    export default {
        name: 'copyright'
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../Copyright/mixinCopyright.scss';

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .copyright {
        /*
            Задать ширину для этого блока с текстом
        */
        display: block;
        font-size: $copyright_text-size;
        line-height: $copyright_text-height;
        font-family: $app_font;
        color: $copyright_text-color;
        @include slice();
    }
</style>