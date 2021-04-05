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
    @import '../NavList/mixinNavList.scss';
    @import '../NavList/optionsNavList.scss';    

    .nav-list {
        font-family: $app_font;
        &__item-box {
            padding: 0 0 20px 0;
        }
        &__self-item.is-first-item {
            @include selfTitle(
                $item-title_bold,
                $item-title_size,
                $item-title_height,
                $item-title_color,
                $item-title_transform
            );
        }
        &__self-item {
            display: block;
            @include selfItem(
                $item_bold,
                $item-size,
                $item_height,
                $item_color
            );
        }
        &__self-item,
        &__self-item.is-first-item {
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    }
</style>