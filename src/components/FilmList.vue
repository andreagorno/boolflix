<template>

    <div>
        <Search @performSearch="searchFilm"/>

        <main class="container films-list">
            <div class="row">
                <div 
                class="col-6 col-md-4 col-lg-3" 
                v-for="film in films"
                :key="film.id">
                    <Film
                        :item="film"
                    />
                </div>
                <div 
                class="col-6 col-md-4 col-lg-3" 
                v-for="serie in series"
                :key="serie.id">
                    <Series
                        :item="serie"
                    />
                </div>
            </div>
        </main>
    </div>

    
</template>

<script>
import axios from "axios"
import Film from "./Film.vue"
import Series from "./Series.vue"
import Search from "./Search.vue"

export default {
    name: "FilmList",

    components: {
        Film,
        Series,
        Search
    },

    data: function () {
        return {
            apiUrlFilms: "https://api.themoviedb.org/3/search/movie",
            apiUrlSeries: "https://api.themoviedb.org/3/search/tv",
            apiTitle: "scrubs",
            films: [],
            series: [],
        }
    },

    created: function () {
       this.getMovies();
    },
    methods: {
        getMovies() {
            axios
            .get(this.apiUrlFilms, {
                params: {
                    api_key: "e99307154c6dfb0b4750f6603256716d",
                    query: this.apiTitle,
                    language: "it-IT"
                }
            })
            
            .then(
                (res) => {
                    // console.log(res.data.results);
                    this.films = res.data.results;
                    console.log(this.films);
                }
            )
            .catch();

            axios
            .get(this.apiUrlSeries, {
                params: {
                    api_key: "e99307154c6dfb0b4750f6603256716d",
                    query: this.apiTitle,
                    language: "it-IT"
                }
            })

            .then(
                (res) => {
                    // console.log(res.data.results);
                    this.series = res.data.results;
                    console.log(this.series);
                }
            )

            .catch();

        },
        searchFilm: function(text) {
            // console.log(text);
            this.apiTitle = text;
            this.getMovies();
        }
    },
}


</script>

<style lang="scss" scoped>
    
    // main {
    //     height: 90vh;
    // }

    .films-list {
        display: flex;
        justify-content: center;
        // align-items: center;
        overflow-y: auto;
    }


</style>