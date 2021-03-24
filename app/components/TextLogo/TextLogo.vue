<template lang='pug'>
    span(class="text-logo") Toxin
</template>

<script>
    export default {
        name: 'TextLogo'
    }
</script>

<style lang='scss' scoped>
    $text_logo_color: #1f2041;
    $text_logo_transform: uppercase; 

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .text-logo {
        display: block;
        color: $text_logo_color;
        text-transform: $text_logo_transform;
        font-style: normal;
        font-weight: bold;
        font-family: 'Montserrat', sans-serif;
        width: 50px;
        order: 1;
        @include slice();
        z-index: 100;
    }

    @media screen and (max-width: 767px) {
        .text-logo {
            width: 100%;
            font-size: 21px;
        }
    }
</style>