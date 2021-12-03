<template>
    <div>
        <Header @getToSearch="getToSearch"></Header>
        <Main :films="films" :tvSeries="tvSeries" :inputSearch="apiParams.query"></Main>
    </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';

import axios from 'axios';

export default {
    name: 'App',
    components: {
        Header,
        Main
    },
    data() {
        return {
            apiUrlSearch: `https://api.themoviedb.org/3/search/`,
            type: ['movie?', 'tv?'],
            rank: [],
            apiParams: {
                api_key: 'd29c9567998ea38ba500431663e2b425',
                language: 'it',
                query: ''
            },
            films: null,
            tvSeries: null,
        }
    },
    mounted() {
    },
    methods: {
        getApiSearch() {
            const requestOne = axios.get(this.apiUrlSearch + this.type[0], {params: this.apiParams});
            const requestTwo = axios.get(this.apiUrlSearch + this.type[1], {params: this.apiParams});

            axios.all([requestOne, requestTwo])
            .then(axios.spread((...response) => {
                this.films = response[0].data.results;
                this.tvSeries = response[1].data.results;
            })).catch(error => {
                console.log(error);
            })
        },
        getToSearch(input) {
            this.apiParams.query = input;
            this.getApiSearch();
        },
        // getApiHome() {
        //     const requestOne = axios.get(this.apiUrlSearch + this.type[0], {params: this.apiParams});
        //     const requestTwo = axios.get(this.apiUrlSearch + this.type[1], {params: this.apiParams});
        //     const requestThree = axios.get(this.apiUrlSearch + this.type[2], {params: this.apiParams});

        //     axios.all([requestOne, requestTwo, requestThree])
        //     .then(axios.spread((...response) => {
        //         this.films = response[0].data.results;
        //         this.tvSeries = response[1].data.results;
        //         this.prova = response[2].data.results;
        //         console.log(this.films);
        //     })).catch(error => {
        //         console.log(error);
        //     })
        // },
    }
}
</script>

<style lang="scss">
@import './assets/style/general.scss'

</style>