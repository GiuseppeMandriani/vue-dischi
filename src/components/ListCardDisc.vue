<template>
    <section class="card container">
        <div v-if="!loading" class="row">
            <div v-for="(disc, index) in discList" :key="index" class="card">
                <Card :details="disc" />
            </div>
        </div>
        <Loader v-else />
    </section>
</template>

<script>
import axios from 'axios'; // Importo Axios per API
import Card from '@/components/Card.vue';
import Loader from '@/components/Loader.vue';

export default {
    name: 'ListCardDisc',
    components: {
        Card,
        Loader,
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
            setTimeout(() => {
                axios
                    .get(this.apiURL)
                    .then(result => {
                        this.discList = result.data.response;
                        this.loading = false;
                        console.log(result.data.response);
                    })
                    .catch(error => {
                        console.log('Errore', error);
                    });
            }, 2000);
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
        flex-basis: calc(100% / 8 - 1rem);

        margin: 0 0.5rem;
        margin-bottom: 1rem;
        padding: 20px 15px;
        background-color: #2e3a46;
    }
}
</style>
