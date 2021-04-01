<template lang="pug">
    div(class="nav-description") {{navDescription}}
</template>

<script>
    export default {
        name: 'description_logo_nav',
        props: {
            navDescription: {
                type: String,
                default: ''
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../DescriptionLogoNav/mixinDescriptionNav.scss';

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .nav-description {
        width: $nav-descrip-text_width;
        font-size: $nav-descrip-text_size;
        line-height: $nav-descrip-text_height;
        font-family: $app_font;
        color: $nav-descrip-text_color;
        @include slice();
    }
</style>