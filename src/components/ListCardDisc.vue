<template>
    <section class="card container">
        <div class="row">
            <div class="card">
                <Card />
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios'; // Importo Axios per API
import Card from '@/components/Card.vue';

export default {
    name: 'ListCardDisc',
    components: {
        Card,
    },

    data() {
        return {
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            discList: [], // Ospiterà  API
            loading: true, // Variabile pre caricamento API
        };
    },

    created() {
        this.getList();
    },

    methods: {
        getList() {
            /**
             * Chiamata API
             */
            axios
                .get(this.apiURL)
                .then(result => {
                    console.log(result.data);
                    this.discList = result.data;
                    this.loading = false;
                })
                .catch(error => {
                    console.log('Errore', error);
                });
        },
    },
};
</script>

<style scoped lang="scss">
.row {
    display: flex;
    flex-wrap: wrap;
    padding-top: 100px;
    padding-bottom: 15px;

    .card {
        flex-basis: calc(100% / 8 - 2rem);
        height: 250px;
        margin: 0 1rem;
    }
}
</style>
