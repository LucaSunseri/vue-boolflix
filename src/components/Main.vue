<template>
    <div>
        <main>
            <div v-if="inputSearch == ''" class="text-center mt-5">Da aggiungere un Home page</div>
            <div v-else class="search">
                <div v-if="films.length !== 0 || tvSeries.length !== 0" class="ls-container">
                    <h3 v-if="films.length !== 0">Film</h3>
                    <div class="ls-container__card">
                        <Card v-for="film in films" :key="film.id"
                            :image="`${imageUrl}${film.poster_path}`"
                            :title="film.title"
                            :originalTitle="film.original_title"
                            :originalLanguage="convertLanguage(film.original_language)"
                            :voteAverage="convertVote(film.vote_average)"
                            :overview="film.overview"
                        />
                    </div>
                    <h3 v-if="tvSeries.length !== 0">Serie Tv</h3>
                    <div class="ls-container__card">
                        <Card v-for="series in tvSeries" :key="series.id"
                            :image="`${imageUrl}${series.poster_path}`"
                            :title="series.name"
                            :originalTitle="series.original_name"
                            :originalLanguage="convertLanguage(series.original_language)"
                            :voteAverage="convertVote(series.vote_average)"
                            :overview="series.overview"
                        />
                    </div>
                </div>
                <div v-else class="ls-no-found">
                    <p>Nessun risultato per la tua ricerca di "{{inputSearch}}"</p>
                    <p>Suggerimenti:</p>
                    <ul>
                        <li>Prova con parole chiave diverse</li>
                        <li>Cerchi un film o un programma TV?</li>
                        <li>Prova a usare il titolo di un film o programma TV</li>
                    </ul>
                </div>
            </div>
            
        </main>

    </div>  
</template>

<script>
import Card from './Card.vue';

export default {
    name: 'Main',
    components: {
        Card,
    },
    data() {
        return {
            imageUrl: 'https://image.tmdb.org/t/p/w185',
        }
    },
    props: {
        films: Array,
        tvSeries: Array,
        inputSearch: String,
    },
    created() {

    },
    computed: {

    },
    methods: {
        convertLanguage(language) {
            if (language === 'en'){
                return 'GB';
            }
            if (language === 'ja'){
                return 'JP';
            }
            if (language === 'ko'){
                return 'KR';
            }
            if (language === 'zh'){
                return 'CN';
            }
            if (language === 'hi'){
                return 'IN';
            }
            return language.toUpperCase();
        },
        
         convertVote(vote) {
             return Math.round(vote/2);
        }
    }
}
</script>

<style lang="scss" scoped>

main {
    height: calc(100vh - 70px)/*80px height header*/;
    overflow: auto;
    color: white;
    background-image: linear-gradient(to bottom,
        lighten(black, 20%),
        lighten(black, 10%),
    );
    .ls-container {
        padding: 50px 5%;
        h3 {
            font-weight: 600;
        }
    }
}

.ls-container__card {
    margin: 25px auto;
    white-space: nowrap;
    overflow-x: auto;
    overflow-y: hidden;
}

.ls-no-found {
    width: 30%;
    margin: 0 auto;
    padding-top: 10%;
}

</style>