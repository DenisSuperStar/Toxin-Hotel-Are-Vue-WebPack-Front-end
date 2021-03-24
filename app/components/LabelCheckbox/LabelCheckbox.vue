<template lang="pug">
    span(class="label-checkbox" :class="uniqClass") {{labelText}}
</template>

<script>
    export default {
        name: 'label_checkbox',
        props: {
            labelText: {
                type: String,
                default: ''
            },
            uniqClass: {
                type: String,
                default: ''
            }
        }
    }
</script>

<style lang="scss" scoped>
    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .label-checkbox {
        display: block;
        width: 192px;
        height: max-content;
        font: bold 14px / 18px 'Montserrat', sans-serif;
        color: rgba(31, 32, 65, 0.5);
        @include slice();
        &--uniq {
            white-space: break-spaces;
        }
    }
</style>