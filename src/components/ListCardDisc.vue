<template>
    <section class="card container">
        <div v-if="!loading" class="row">
            <div v-for="(disc, index) in discList" :key="index" class="card">
                <Card :details="disc" />
            </div>
        </div>
        <Loader v-else label="Loading...">
            <img src="@/assets/logo.png" alt="Logo Spotify" />
        </Loader>
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
@import '@/styles/vars';
.row {
    display: flex;
    flex-wrap: wrap;
    padding-top: 100px;
    padding-bottom: 15px;
    flex-shrink: 0;
    justify-content: center;
    max-width: 100%;

    .card {
        flex-basis: calc(100% / 8 - 1rem);
        max-width: 100%;

        margin: 0 0.5rem;
        margin-bottom: 1rem;
        padding: 20px 15px;
        background-color: $secondary-color;
    }
}

@media screen and (max-width: 1024px) {
    .row .card {
        flex-basis: calc(100% / 6 - 1rem);
    }
}
@media screen and (max-width: 768px) {
    .row .card {
        flex-basis: calc(100% / 4 - 1rem);
    }
}
</style>
