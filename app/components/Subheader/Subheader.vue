<template lang="pug">
    div(class="subheader")
        div(
            class="subheader__old" 
            ref='subheader' 
            @mouseover='readyFlowingText'
        ) {{subheaderText}}
        div(
            class="subheader__changing is-share" 
            ref="symbols_box"
        )
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
                    text_item.setAttribute('class', 'subheader__one');

                    text_item.classList.add('is-move-character');
                    text_item.prepend(letter);
                    items.append(text_item);

                    if (text_item.innerHTML == ' ') {
                        text_item.classList.add('is-shifting');
                    }
                }
            }
        }
    }
</script>

<style lang="scss">
    @import '../../mixinApp.scss';
    @import '../Subheader/mixinSubheader.scss';
    @import '../Subheader/optionsSubheader.scss';

    @mixin slice {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
    
    .subheader {
        &__old,
        &__changing {
            width: 196px;
            cursor: pointer;
        }
        &__old {
          @include slice();  
        }
        &__old,
        &__one.is-move-character {
            display: block;
            @include subheader(
                $subheader_bold,
                $subheader_size,
                $subheader_height,
                $subheader_color,
                $subheader_transform
            );
            font-family: $app_font;
        }
        &__changing {
            position: relative;
            display: flex;
        }
        &__changing.is-share:hover > &__one.is-move-character {
            /*
                the color new state of animation
            */
            color: $subheader_color_new_state;
            transition: all 0.2s ease-in-out;
            &::after {
                width: 100%;
                /*
                    the background new state of animation
                */
                background: $subheader_background_new_state;
            }
        }
        &__one.is-move-character {
            margin-right: -0.47px;
            &::after {
                content: '';
                width: 0;
                position: absolute;
                top: 0;
                bottom: 0;
                left: 0;
                z-index: -5;
                transition: all 0.5s ease-in-out;
            }
        }
        &__one.is-shifting {
            margin-right: 5px;
        }
    }

    $start: 1;
    $finish: 25;

    @for $j from $start to $finish {
        .subheader {
            &__changing.is-share:hover > &__one.is-move-character:nth-child(#{$j})::after {
                $delay: 100 * $j;
                transition-delay: $delay + ms;
            }
        }
        .subheader {
            &__changing.is-share:hover > &__one.is-move-character:nth-child(#{$j}) {
                $delay_copy: 110 * $j;
                $rotation: ($j * 0.01);
                transition-delay: $delay_copy + ms;
                transform: rotate($rotation + deg);
            }
        } 
    }
</style>