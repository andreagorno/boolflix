<template>

    <div>
        <header>
            <input type="text" placeholder="Cosa stai Cercando?">
            <button>Submit</button>
        </header>

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
            </div>
        </main>
    </div>

    
</template>

<script>
import axios from "axios"
import Film from "./Film.vue"

export default {
    name: "FilmList",

    components: {
        Film
    },

    data: function () {
        return {
            apiUrl: "https://api.themoviedb.org/3/search/movie",
            films: []
        }
    },

    created: function () {
        axios
            .get(this.apiUrl, {
                params: {
                    api_key: "e99307154c6dfb0b4750f6603256716d",
                    query: "ritorno",
                    language: "it-IT"
                }
            })
            .then(
                (res) => {
                    // console.log(res.data.results);
                    this.films = res.data.results;
                    // console.log(this.films);
                }
            )
    }
}


</script>

<style lang="scss" scoped>
    header {
        display: flex;
        flex-direction: row-reverse;
        align-items: center;
        height: 10vh;
        background-color: black;

        input,
        button {
            padding: 5px;
            margin-right: 10px;
        }
    }

    main {
        height: 90vh;
    }

    .films-list {
        display: flex;
        justify-content: center;
        align-items: center;
    }


</style>