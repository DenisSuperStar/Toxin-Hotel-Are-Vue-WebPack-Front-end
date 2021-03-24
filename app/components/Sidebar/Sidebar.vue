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
        margin: 0 59px 0 140px;
    }
    
    @media screen and (min-width: 1200px) and (max-width: 1440px) {
        .sidebar {
            width: 266px;
            margin: 0 59px 0 auto;
        }
    }

    @media screen and (min-width: 992px) and (max-width: 1199px) {
        .sidebar {
            margin: 0 calc(59px / 2.4) 0 30px;
        }
    }

    @media screen and (max-width: 991px) {
        .sidebar {
            margin: 0;
        }
    }
</style>