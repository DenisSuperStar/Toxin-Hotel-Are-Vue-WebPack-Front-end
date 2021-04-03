<template lang="pug">
    div(class="title-gallery") Номера, которые мы для вас подобрали
</template>

<script>
    export default {
        name: 'title_gallery'
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../TitleGallery/mixinTitleGallery.scss';

    .title-gallery {
        font-weight: $title-gallery_bold;
        font-size: $title-gallery_size;
        line-height: $title-gallery_height-text;
        font-family: $app_font;
        color: $title-gallery_color;
        text-transform: $title-gallery_transform;
    }
</style>