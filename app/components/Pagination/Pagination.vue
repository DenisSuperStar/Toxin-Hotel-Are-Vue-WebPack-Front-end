<template lang="pug">
    div(class="just-pagination")
        span(class=`
                just-pagination__control 
                just-pagination__control--prev`
                v-if="page != 1"
                @click="page--"
        )
        span(
            class="just-pagination__button"
            v-for="(number_page, id) in pages.slice(page - 1, page + 2)"
            @click="page = number_page"
            v-if="number_page != pages.length"
            :class="{'is-active-button': page == (page + id)}"
            :data-count="page"
        ) {{number_page}}
        span(
            class="just-pagination__button"
            v-for="number_page in pages.slice(pages.length - 1, pages.length)"
            @click="page = number_page"
            :class="{'is-active-button': page == pages.length}"
            :data-count="page"
        ) {{number_page}}
        span(
            class=`
                just-pagination__control 
                just-pagination__control--next`
                @click="page++"
                v-if="page < pages.length"
        )
</template>

<style lang="scss" scoped>
    @import '../Pagination/mixinPagination.scss';

    @mixin flexible($align, $item) {
        display: flex;
        justify-content: $align;
        align-items: $item;
    }

    /*paginator не компонент, а простой блок, сделать простым блоком*/

    .just-pagination {
        width: 100%;
        display: flex;
        justify-content: center;
        &__button,
        &__control {
            position: relative;
            @include flexible(center, center);
            width: $pagination_width;
            height: $pagination_height;
        }
        &__button {
            background: $pagination_button_default_background;
            color: $pagination_button_default_color-text;
            cursor: pointer;
        }
        &__button.is-active-button {
            background: $pagination_active-button_background;
            color: $pagination_active-button_color-text;
            border-radius: $pagination_active-button_round;
        }
        &__control {
            &--prev,
            &--next {
                background: $pagintion_background_control;
                border-radius: $pagintion_round_control; 
            }
            &--prev::after {
                content: $pagination_prev-control_img;
            }
            &--next::after {
                content: $pagination_next-control_img;
            }
            &--prev::after,
            &--next::after {
                @include flexible(center, center);
                width: $pagination_control_width;
                height: $pagination_control_height;
                font-size: $pagination_size_icon-control;
                line-height: $pagintion_height_icon-control;
                color: $pagintion_color_icon-control;
                font-family: $pagintion_icon-control_type-font;
            }
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1450px) {
        .just-pagination {
            display: flex;
            justify-content: space-around;
            & > &__button:first-child {
                margin: 0 0 0 48.26px;
            }
            & > &__control {
                &--next {
                    margin: 0 auto 0 0;
                }
            }
        }
    }

    @media screen and (min-width: 1451px) and (max-width: 1600px) {
        .just-pagination {
            display: flex;
            justify-content: flex-end;
        }
    }
</style>

<script>
    export default {
        name: 'pagination',
        data: () => {
            return {
                id: 0,
                posts: [''],
                page: 1,
                per_page: 9,
                pages: []
            }
        },
        methods: {
            getPosts: function() {
                for (let j = 0; j < 130; j++) {
                    this.posts.push({j});
                }
            },
            setPages: function() {
                const count_pages = Math.ceil(this.posts.length / this.per_page);
                for (let index = 1; index <= count_pages; index++) {
                    this.pages.push(index);
                }
            },
            paginate: function(posts) {
                const from = (this.page * this.per_page) - this.per_page;
                const to = (this.page * this.per_page);

                return posts.slice(from, to);
            }
        },
        computed: {
            displayPosts: function() {
                return this.paginate(this.posts);
            }
        },
        watch: {
            posts: function() {
                this.setPages();
            }
        },
        created: function() {
            this.getPosts();
        }
    }
</script>