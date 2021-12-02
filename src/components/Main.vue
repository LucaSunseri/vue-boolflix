<template>
    <div>
        <main>
            <div class="container">
                <h2>Film</h2>
                <div class="container__card">
                    <!-- <h3>Titolo: {{film.title}}</h3>
                    <h4>Titolo Originale: {{film.original_title}}</h4>
                    <h4>Lingua: <img class="flag" :alt="film.original_language" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + stampFlag(film.original_language) + `.svg`">
                    </h4>
                    <h4>Voto: {{film.vote_average}}</h4> -->
                    <Card v-for="film in films" :key="film.id"
                        :image="`${imageUrl}${film.poster_path}`"
                        :title="film.title"
                    />
                </div>
                <h2>Serie Tv</h2>
                <div v-for="series in tvSeries" :key="series.id" class="container__card">
                    <h3>Titolo: {{series.name}}</h3>
                    <h4>Titolo Originale: {{series.original_name}}</h4>
                    <h4>Lingua: <img class="flag" :alt="series.original_language" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + stampFlag(series.original_language) + `.svg`">
                    </h4>
                    <h4>Voto: {{convertVote(series.vote_average)}}</h4>
                    <!-- <Card v-for="series in tvSeries" :key="series.id"
                        :image="`${imageUrl}${series.poster_path}`"
                        :title="series.name"
                    /> -->
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
        stampFlag(language) {
            if (language === 'en'){
                return 'GB';
            }
            if (language === 'ja'){
                return 'JP';
            }
            if (language === 'ko'){
                return 'KR';
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
        .flag {
            margin-left: 5px;
            vertical-align: text-bottom;
            height: 25px;
            width: 25px;
        }
    }
}

.container__card {
    margin: 25px auto;
    display: flex;
    overflow-y: auto;
}

</style>