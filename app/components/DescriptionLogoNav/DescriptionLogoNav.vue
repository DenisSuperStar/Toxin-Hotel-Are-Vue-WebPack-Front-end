<template lang="pug">
    div(class="nav-description") {{navDescription}}
</template>

<script>
    export default {
        name: 'description_logo_nav',
        props: {
            navDescription: {
                type: String,
                default: ''
            }
        }
    }
</script>

<style lang="scss" scoped>
    .nav-description {
        width: 260px;
        font-size: 14px;
        line-height: 24px;
        font-family: 'Montserrat', sans-serif;
        color: rgba(31, 32, 65, 0.75);
    }
</style>