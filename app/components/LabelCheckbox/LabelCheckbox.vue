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
    @import '../../mixinApp.scss';
    @import '../LabelCheckbox/mixinLabelCheckbox.scss';

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    @mixin checkboxLabel() {
        
    }

    .label-checkbox {
        display: block;
        width: $label-checkbox_width;
        font-weight: $label-checkbox_bold-text;
        font-size: $label-checkbox_text-size;
        line-height: $label-checkbox_text-height;
        font-family: $app_font;
        color: $label-checkbox_text-color;
        @include slice();
        &--uniq {
           white-space: break-spaces; 
        }
    }
</style>