<template lang="pug">
    div(class="subheader-animate")
        div(class="subheader-animate__subheader" ref='subheader' @mouseover='readyFlowingText') {{subheaderText}}
        div(class="subheader-animate__break share" ref="symbols_box")
</template>

<script>
    export default {
        name: 'subheader',
        props: {
            subheaderText: String
        },
        methods: {
            readyFlowingText: function() {
                const subheader = this.$refs.subheader;
                const title = subheader;
                const symbols_box = this.$refs.symbols_box;
                const items = symbols_box;
                
                title.style.display = 'none';
                const getting_letters = title.innerHTML.split('');

                for (const letter of getting_letters) {
                    const text_item = document.createElement('span');

                    text_item.classList.add('subheader-animate__character');
                    text_item.prepend(letter);
                    items.append(text_item);

                    if (text_item.innerHTML == ' ') {
                        text_item.classList.add('subheader-animate__character--spaced');
                    }
                }
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

    .subheader-animate {
        &__subheader {
            width: 196px;
            text-transform: uppercase;
            color: #1f2041;
            font: bold 12px / 15px 'Montserrat', sans-serif;
            @include slice();
            cursor: pointer;
        }
        &__break {
            position: relative;
            display: flex;
            width: 196px;
            cursor: pointer;
        }
    }
</style>