<template lang="pug">
    aside(class="nav-list")
        template(v-for="(data_item, index) in dataList")
            div(class="nav-list__item-box")
                span(
                    class="nav-list__self-item" 
                    :class="{'is-first-item': ++index == 1}"
                ) {{data_item}}
</template>

<script>
    export default {
        name: 'nav_list',
        props: {
            dataList: {
                type: Array,
                default: []
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../../mixinApp.scss';
    @import '../NavList/mixinFooterNavList.scss';    

    @mixin titleItem() {

    }

    @mixin item() {
        
    }

    .nav-list {
        font-family: $app_font;
        &__item-box {
            padding: 0 0 20px 0;
        }
        &__self-item {
            display: block;
            font-weight: $item_bold_of_nav-list;
            font-size: $item_size_of_nav-list;
            line-height: $item_height_of_nav-list;
            color: $item_color_of_nav-list;
        }
        &__self-item.is-first-item {
            font-weight: $title_bold_of_nav-list;
            font-size: $title_size_of_nav-list;
            line-height: $title_height_of_nav-list;
            color: $title_color_of_nav-list;
            text-transform: $title_action-text_of_nav-list;
        }
        &__self-item,
        &__self-item.is-first-item {
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    }
</style>