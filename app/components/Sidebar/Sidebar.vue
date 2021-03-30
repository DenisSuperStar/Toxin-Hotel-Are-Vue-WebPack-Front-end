<template lang="pug">
    div(class="sidebar")
        sidebar_box
</template>

<script>
    import sidebar_box from '../SidebarContent/SidebarContent.vue';

    export default {
        name: 'sidebar',
        components: {
            sidebar_box
        }
    }
</script>

<style lang="scss" scoped>
    .sidebar {
        width: 100%;
    }

    @media screen and (min-width: 1200px) and (max-width: 1470px) {
        .sidebar {
            width: 266px;
        }
    }

    @media screen and (min-width: 1200px) and (max-width: 1400px) {
        .sidebar {
            margin: 0;
        }
    }
</style>