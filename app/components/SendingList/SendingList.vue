<template lang="pug">
    aside(class="sending-list")
        div(class="sending-list__content")
            nav_list(:data-list="subscribe")
            nav_description(:nav-description="nav_description_subscribe")
            div(class="sending-list__form-box")
                form_sending



</template>

<script>
    import form_sending from '../FormSending/FormSending.vue';
    import nav_list from '../NavList/NavList.vue';
    import nav_description from '../DescriptionLogoNav/DescriptionLogoNav.vue';

    export default {
        name: 'sending_list',
        components: {
            form_sending,
            nav_list,
            nav_description
        },
        data: () => {
            return {
                subscribe: [
                    'Подписка'
                ],
                nav_description_subscribe: 'Получайте специальные предложения и новости сервиса'
            }
        }
    }
</script>

<style lang="scss" scoped>
    .sending-list {
        &__form-box {
            padding: 0 0 20px 0;
        }
    }
</style>