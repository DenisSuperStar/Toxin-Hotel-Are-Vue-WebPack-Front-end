<template lang="pug">
    div(
        class=`
            logo
            logo--visually-modified
    `)
        div(
            class=`
                logo__item
                logo__item--visually-modified
                logo__item--more
                logo__item--visually-modified-more
                logo__item--auto-rotated-more`
        )
        div(
            class=`
                logo__item
                logo__item--visually-modified
                logo__item--less
                logo__item--visually-modified-less
                logo__item--auto-rotated-less
            `
        )
        
</template>

<script>
    export default {
        name: 'logo'
    }
</script>

<style lang="scss" scoped>
    .logo {
        position: relative;
        width: 40px;
        height: 40px;

        border-width: 1px;
        border-style: solid;
        border-color: #1f2041;
        &--visually-modified {
            border-width: 2px;
            border-style: solid;
            border-color: #8ba4f9;

            border-radius: 50%;
        }
        &__item {
            width: 11.76px;
            height: 11.76px;
            
            border-right-width: 1px;
            border-right-style: solid;
            border-right-color: #1f2041;
            &--visually-modified {
                border-right-width: 2px;
                border-right-style: solid;
                border-right-color: #8ba4f9;
            }
            &--more {
                width: 11.76px;
                height: 11.76px;
            }
            &--visually-modified-more {
                border-radius: 0 100px 500px 100px;
            }
            &--auto-rotated-more {
                transform: rotate(-70deg);
                margin: 14.79px 0 0 7.4px;
            }
            &--less {
                width: 9.12px;
                height: 9.12px;

                position: absolute;
                top: 0;
            }
            &--visually-modified-less {
                border-radius: 0 100px 100px 0;
            }
            &--auto-rotated-less {
                transform: rotate(240deg);
                margin: 14px 0 0 20px;
            }
        }
    }
</style>