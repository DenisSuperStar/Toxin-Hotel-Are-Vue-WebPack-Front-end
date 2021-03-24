<template lang="pug">
    aside(class="nav-list")
        template(v-for="(data_item, index) in dataList")
            div(class="nav-list__item-box")
                span(class="nav-list__self-item" :class="{'is-first-item': ++index == 1}") {{data_item}}
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
    .nav-list {
        font-family: 'Montserrat', sans-serif;
        &__item-box {
            padding: 0 0 20px 0;
        }
        &__self-item {
            display: block;
            font-size: 14px;
            font-weight: normal;
            color: rgba(31, 32, 65, 0.5);
            line-height: 17px;
        }
        &__self-item.is-first-item {
            font-size: 12px;
            font-weight: bold;
            color: #1f2041;
            text-transform: uppercase;
            line-height: 15px;
        }
    }
</style>