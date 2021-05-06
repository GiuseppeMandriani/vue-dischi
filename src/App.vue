<template>
    <div id="app">
        <Header message="Dischi del Mese" />
    </div>
</template>

<script>
import Header from '@/components/Header.vue';
export default {
    name: 'App',
    components: {
        Header,
    },
};
</script>

<style lang="scss">
@import '~@fontsource/montserrat/index.css'; // Default 400
@import '~@fontsource/montserrat/700.css'; // Scelto da me

@import '@/styles/general'; // Importo file general
</style>
