<template>
    <div>
        <main>
            <div class="container">
                <h2>Film</h2>
                <div v-for="film in films" :key="film.id" class="film">
                    <h3>Titolo: {{film.title}}</h3>
                    <h4>Titolo Originale: {{film.original_title}}</h4>
                    <h4>Lingua: <img class="flag" :alt="film.original_language" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + stampFlag(film.original_language) + `.svg`">
                    </h4>
                    <h4>Voto: {{film.vote_average}}</h4>
                </div>
                <h2>Serie Tv</h2>
                <div v-for="series in tvSeries" :key="series.id" class="serie-tv">
                    <h3>Titolo: {{series.name}}</h3>
                    <h4>Titolo Originale: {{series.original_name}}</h4>
                    <h4>Lingua: <img class="flag" :alt="series.original_language" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + stampFlag(series.original_language) + `.svg`">
                    </h4>
                    <h4>Voto: {{series.vote_average}}</h4>
                </div>
            </div>
        </main>

    </div>  
</template>

<script>

export default {
    name: 'Main',
    data() {
        return {


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
        }
    }
}
</script>

<style lang="scss" scoped>

main {
    height: calc(100vh - 80px)/*80px height header*/;
    overflow: auto;
    color: white;
    background-image: linear-gradient(to bottom,
        lighten(black, 20%),
        lighten(black, 10%),
    );
    .container {
        div {
            padding: 20px;
        }
        .flag {
            margin-left: 5px;
            vertical-align: text-bottom;
            height: 25px;
            width: 25px;
        }
    }
}

</style>