<template lang="pug">
    div(class="grid")
        sidebar
        card_gallery
</template>

<script>
    import sidebar from '../Sidebar/Sidebar.vue';
    import card_gallery from '../GridItems/GridItems.vue';

    export default {
        name: 'grid',
        components: {
            card_gallery,
            sidebar
        }
    }
</script>

<style lang="scss" scoped>
    .grid {
        display: flex;
    }
    
    @media screen and (max-width: 1140px) {
        .grid {
            display: flex;
            flex-flow: column;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1470px) {
        .grid {
            display: flex;
            justify-content: space-between;
        }
    }

    @media screen and (min-width: 1400px) and (max-width: 1470px) {
        .grid {
            padding: 0 0 0 140px;
        }
    }
</style>