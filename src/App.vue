<template>
    <div>
        <Header @getToSearch="getToSearch"></Header>
        <main v-if="loading"></main>
        <Main
            v-else
            :inputSearch="apiParams.query"
            :foundSearch="foundSearch"
            :films="films"
            :tvSeries="tvSeries"
            :topWeekFilms="topWeekFilms"
            :topWeekTvSeries="topWeekTvSeries"
            :upcomingFilms="upcomingFilms"
        >
        </Main>
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

import axios from "axios";

export default {
    name: "App",
    components: {
        Header,
        Main,
    },
    data() {
        return {
            apiUrlSearch: `https://api.themoviedb.org/3/search/`,
            apiUrlTrending: `https://api.themoviedb.org/3/trending/`,
            type: ["movie?", "tv?"],
            apiParams: {
                api_key: "d29c9567998ea38ba500431663e2b425",
                language: "it",
                query: "",
            },
            films: [],
            tvSeries: [],
            topWeekFilms: [],
            topWeekTvSeries: [],
            upcomingFilms: [],
            loading: true,
            foundSearch: false,
        };
    },
    mounted() {
        this.getApiHome();
    },
    methods: {
        // Get Api for Search
        getApiSearch() {
            const request1 = axios.get(this.apiUrlSearch + this.type[0], {
                params: this.apiParams,
            });
            const request2 = axios.get(this.apiUrlSearch + this.type[1], {
                params: this.apiParams,
            });

            axios
                .all([request1, request2])
                .then(
                    axios.spread((...response) => {
                        this.films = response[0].data.results;
                        this.tvSeries = response[1].data.results;
                        if (this.films.length == 0 && this.tvSeries == 0) {
                            this.foundSearch = false;
                        }
                    })
                )
                .catch((error) => {
                    console.log(error);
                });
        },
        getToSearch(input) {
            this.apiParams.query = input;
            this.getApiSearch();
            this.foundSearch = true;
        },
        // Get Api for HomePage
        getApiHome() {
            const request1 = axios.get(
                "https://api.themoviedb.org/3/trending/movie/week?api_key=d29c9567998ea38ba500431663e2b425"
            );
            const request2 = axios.get(
                "https://api.themoviedb.org/3/trending/tv/week?api_key=d29c9567998ea38ba500431663e2b425"
            );
            const request3 = axios.get(
                "https://api.themoviedb.org/3/movie/upcoming?api_key=d29c9567998ea38ba500431663e2b425&language=it&page=1"
            );

            axios
                .all([request1, request2, request3])
                .then(
                    axios.spread((...response) => {
                        this.topWeekFilms = response[0].data.results;
                        this.topWeekTvSeries = response[1].data.results;
                        this.upcomingFilms = response[2].data.results;
                        this.loading = false;
                    })
                )
                .catch((error) => {
                    console.log(error);
                });
        },
    },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";

main {
    height: calc(100vh - 70px) /*80px height header*/;
    background-image: linear-gradient(
        to bottom,
        lighten(black, 20%),
        lighten(black, 10%)
    );
}
</style>
