<template>
    <div id="app">
        <!-- Header -->
        <Header message="Dischi del Mese" />

        <!-- Main -->
        <main>
            <ListCardDisc />
        </main>
    </div>
</template>

<script>
import Header from '@/components/Header.vue';
import ListCardDisc from '@/components/ListCardDisc.vue';
export default {
    name: 'App',
    components: {
        Header,
        ListCardDisc,
    },
};
</script>

<style lang="scss">
@import '~@fontsource/montserrat/index.css'; // Default 400
@import '~@fontsource/montserrat/700.css'; // Scelto da me

@import '@/styles/general'; // Importo file general
</style>
