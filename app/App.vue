<template lang="pug">
    div(id='app')
        site_header
        site_content
        site_footer
</template>

<script>
    import site_header from '../app/components/TheHeader/TheHeader.vue';
    import site_content from '../app/components/TheContent/TheContent.vue';
    import site_footer from '../app/components/TheFooter/TheFooter.vue';

    export default {
        name: 'app',
        components: {
            site_header,
            site_content,
            site_footer
        }
    }
</script>

<style lang="scss">
    /*
        set box-sizing
    */
    *,
    *::before,
    *::after {
        box-sizing: border-box;
    }
    /*
        set focus event
    */
    *:focus {
        outline: none;
    }
    /*
        settings default for the body
    */
    body {
        min-height: 100vh;
        scroll-behavior: smooth;
    }
    /*
        remove indents of list
    */
    ul,
    li {
        padding: 0;
    }
    /*
        remove outer indents of any elements
    */
    .page,
    h1,
    h2,
    h3,
    h4,
    p,
    ul,
    li {
        margin: 0;
    }
    /*
        remove standart stylization for ul, li
    */
    ul,
    li {
        list-style: none;
    }
    /*
        this links without class name reset to default styles
    */
    a:not([class]) {
        text-decoration-skip-ink: auto;
    }
    /*
        easier work with an image
    */
    img {
        display: block;
        max-width: 100%;
    }
    /*
        it inherit fonts for input and buttons
    */
    input,
    button {
        font: inherit;
    }
</style>