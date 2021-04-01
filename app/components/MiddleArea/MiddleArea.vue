<template lang="pug">
    main(class="content-site")
        article(class="content-site__content")
            grid_box
        div(class="content-site__pagination-box")
            pagination
            pagination_text

</template>

<script>
    import grid_box from '../Grid/Grid.vue';
    import pagination from '../Pagination/Pagination.vue';
    import pagination_text from '../PaginationText/PaginationText.vue';

    export default {
        name: 'central_area',
        components: {
            grid_box,
            pagination,
            pagination_text
        }    
    }
</script>

<style lang="scss" scoped>
    .content-site {
        min-width: 350px;
    }

    .content-site {
        &__pagination-box {
            padding: 40.94px 0 104.56px 0;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1450px) {
        .content-site {
            &__pagination-box {
                padding: 40.94px 0 104.56px 50%;
            }
        }
    }

    @media screen and (min-width: 1451px) and (max-width: 1600px) {
        .content-site {
            &__pagination-box {
                padding: 40.94px 470.74px 104.56px 0;
            }
        }
    }
</style>