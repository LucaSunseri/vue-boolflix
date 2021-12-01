<template>
    <div>
        <main>
            <div class="container">
                <div v-for="film in films" :key="film.id" class="film">
                    <h3>Titolo: {{film.title}}</h3>
                    <h4>Titolo Originale: {{film.original_title}}</h4>
                    <h4>Lingua: {{film.original_language}}</h4>
                    <h4>Voto: {{film.vote_average}}</h4>
                </div>
            </div>
        </main>

    </div>  
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    data() {
        return {
            films: [],
        }
    },
    props: {
        toSearch: String
    },
    created() {
        
    },
    computed: {
        resetToSearch() {
            return this.getApi();
        }

    },
    methods: {
        getApi() {
           axios.get(`https://api.themoviedb.org/3/search/movie?&api_key=d29c9567998ea38ba500431663e2b425&query=${this.toSearch}`)
           .then(response => {
               this.films = response.data.results;
               console.log(this.films);
           })
           .catch(error => {
               console.log(error);
           })
        }
    }
}
</script>

<style lang="scss" scoped>

main {
    height: calc(100vh - 80px)/*80px height header*/;
    overflow: auto;
    background-color: rgba(136, 172, 65, 0.568);
    .container {
        padding: 50px;
        div {
            padding: 20px;
        }
    }
}

</style>