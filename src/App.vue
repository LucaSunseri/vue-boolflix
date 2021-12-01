<template>
    <div>
        <Header @getToSearch="getToSearch"></Header>
        <Main :films="films"></Main>
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
            films: [],
        }
    },
    methods: {
        getToSearch(input) {
            axios.get(`https://api.themoviedb.org/3/search/movie?&api_key=d29c9567998ea38ba500431663e2b425&query=${input}`)
           .then(response => {
               this.films = response.data.results;
               console.log(this.films);
           })
           .catch(error => {
               console.log(error);
           })
        },
    }
}
</script>

<style lang="scss">
@import './assets/style/general.scss'

</style>