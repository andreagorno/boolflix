<template>

    <div>
        <div v-if="!intro">
            <Search @performSearch="searchFilm"/>

            <main >
                <div class=" films-list">
                    
                    <Film
                        v-for="film in films"
                        :key="film.id"
                        :item="film"
                    />
                    
                    <Series
                        v-for="serie in series"
                        :key="serie.id"
                        :item="serie"
                    />
                    
                </div>
            </main>
        </div>

        <Intro v-else/>
    </div>
                
</template>
                

    

<script>
import axios from "axios"
import Film from "./Film.vue"
import Series from "./Series.vue"
import Search from "./Search.vue"
import Intro from "./Intro.vue";

export default {
    name: "FilmList",

    components: {
        Film,
        Series,
        Search,
        Intro
    },

    data: function () {
        return {
            apiUrlFilms: "https://api.themoviedb.org/3/search/movie",
            apiUrlSeries: "https://api.themoviedb.org/3/search/tv",
            apiTitle: "short",
            films: [],
            series: [],
            intro: true
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
                    // console.log(this.films);
                    this.films = res.data.results;
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
                    // console.log(this.series);
                    this.series = res.data.results;
                    setTimeout( () => {
                        this.intro = false;
                    },2000)
                    
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
    
    main {
        height: 90vh;
        padding-top: 12vh;
    }

    .films-list {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        overflow-y: auto;
    }

</style>

        
        