<template lang="pug">
    div(class="pagination-text") 1 - 12 из 100+ вариантов аренды
</template>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../PaginationText/mixinPaginationText.scss';

    .pagination-text {
        display: flex;
        justify-content: center;
        padding: 0;
        font-size: $pagination-text_size;
        line-height: $pagination-text_height;
        color: $pagination-text_color;
        font-family: $app_font;
    }

    @media screen and (min-width: 1200px) and (max-width: 1450px) {
        .pagination-text {
            display: flex;
            justify-content: flex-start;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1450px) {
        .pagination-text {
            padding: 0 0 0 48.26px;
        }
    }

    @media screen and (min-width: 1451px) and (max-width: 1600px) {
        .pagination-text {
            display: flex;
            justify-content: flex-end;
        }
    }
</style>

<script>
    export default {
      name: 'pagination_text'  
    }
</script>