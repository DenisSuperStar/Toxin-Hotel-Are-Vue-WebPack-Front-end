<template lang="pug">
    main(class="central-area")
        article(class="central-area__content")
            grid_box
        div(class="central-area__paginator-box")
            div(class="central-area__paginator")
                pagination

</template>

<script>
    import grid_box from '../Grid/Grid.vue';
    import pagination from '../Pagination/Pagination.vue';

    export default {
        name: 'central_area',
        components: {
            grid_box,
            pagination
        }    
    }
</script>

<style lang="scss" scoped>
    /*
        Удалить pagintor block
        rename paginator-box to pagination
    */
    .central-area {
        min-width: 350px;
        &__paginator-box {
            padding: 40.94px 0 104.56px 50%;
        }
    }

    @media screen and (max-width: 1199px) {
        .central-area {
            &__paginator-box {
                padding: 40.94px 0 104.56px 50px;
            }
        }
    }

    @media screen and (min-width: 1451px) and (max-width: 1600px) {
        .central-area {
            &__paginator-box {
                padding: 40.94px 470.74px 104.56px 0;
            }
        }
    }

    @media screen and (min-width: 1601px) {
        .central-area {
            &__paginator-box {
                padding: 40.94px 0 104.56px 0;
            }
        }
    }
</style>