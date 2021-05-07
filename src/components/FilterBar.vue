<template>
    <section>
        <div class="search">
            <label for="type"></label>
            <div class="wrap-select">
                <select name="type" id="type">
                    <option
                        v-for="(disc, index) in getDisc"
                        :key="index"
                        :value="'all' + disc"
                        @change="$emit('filter')"
                        >{{ disc }}</option
                    >
                    >
                </select>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'FilterBar',
    props: {
        details: Array,
    },
    data() {
        return {
            options: '',
            generi: ['All'],
            type: null,
        };
    },

    computed: {
        getDisc() {
            this.details.forEach(genre => {
                this.type = genre.genre;
                if (!this.generi.includes(this.type)) {
                    this.generi.push(this.type);
                    this.options += genre.genre;
                }
            });
            console.log(this.generi);
            console.log(this.options);
            return this.generi;
        },
    },
};
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';
.search {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80px;
    color: #6a6e75;

    .wrap-select {
        margin-left: 1rem;
        position: relative;
        &::before {
            content: '';
            position: absolute;
            top: 50%;
            right: 10px;
            transform: translateY(-25%);
            border: 5px solid transparent;
            border-top: 5px solid $brand-color;
        }
    }
}

.wrap-select select {
    appearance: none;
    outline: none;
    width: 200px;
    height: 40px;
    padding-right: 25px;
    padding-left: 10px;
    font-size: 1rem;
    font-weight: 400;
    color: &secondary-color;
    border: none;
    color: $brand-color;
    border: 1px solid $brand-color;
    background: transparent;
    text-transform: capitalize;
    text-overflow: ellipsis;
    position: relative;
    cursor: pointer;
    letter-spacing: 1px;
}
</style>
