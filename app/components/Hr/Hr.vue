<template lang="pug">
    div(class="hl")
</template>

<script>
    export default {
        name: 'hl'
    }
</script>

<style lang="scss" scoped>
    @import '../Hr/mixinHr.scss';

    .hl {
        width: $hr_width;
        height: $hr_height;
        background: $hr_background;
    }
</style>