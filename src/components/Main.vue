<template>
    <div>
        <main>
            <div class="container">
                <h2 v-if="films.length !== 0">Film</h2>
                <div class="container__card">
                    <Card v-for="film in films" :key="film.id"
                        :image="`${imageUrl}${film.poster_path}`"
                        :title="film.title"
                        :originalTitle="film.original_title"
                        :originalLanguage="convertLanguage(film.original_language)"
                        :voteAverage="convertVote(film.vote_average)"
                        :overview="film.overview"
                    />
                </div>
                <h2 v-if="tvSeries.length !== 0">Serie Tv</h2>
                <div class="container__card">
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
        tvSeries: Array
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
    .container {
        padding: 50px;
        h2 {
            font-weight: 600;
        }
    }
}

.container__card {
    margin: 25px auto;
    white-space: nowrap;
    overflow-x: auto;
    overflow-y: hidden;
}

</style>