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
    @import '../TitleGallery/optionsTitle.scss';

    .title-gallery {
        @include title-gallery(
            $title-gallery_bold,
            $title-gallery_size,
            $title-gallery_text-height,
            $title-gallery_color
        );
        font-family: $app_font;
    }
</style>