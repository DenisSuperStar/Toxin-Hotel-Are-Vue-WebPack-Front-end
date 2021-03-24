<template lang="pug">
    div(class="grid")
        sidebar
        card_area
</template>

<script>
    import sidebar from '../Sidebar/Sidebar.vue';
    import card_area from '../GridItems/GridItems.vue';

    export default {
        name: 'grid',
        components: {
            card_area,
            sidebar
        }
    }
</script>

<style lang="scss" scoped>
    .grid {
        display: flex;
    }

    @media screen and (max-width: 950px) {
        .grid {
            display: flex;
            flex-flow: column;
        }
    }
</style>