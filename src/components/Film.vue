<template>
    <div class=" pb-4 card">
        <div>
            <img :src="getImage()">
            <div class="info">
                <div>
                    <span>Titolo: </span>
                    {{ item.title }}
                </div>
                <div>
                    <span>Titolo Originale: </span>
                    {{ item.original_title }}
                </div>
                <div v-if="avaibleFlags.includes(item.original_language)">
                    <img 
                    class="flag"
                    :src="require(`../assets/images/${item.original_language}.png`)" 
                    :alt="`bandiera ${item.original_language}`"
                    >
                </div>
                <div v-else> {{ item.original_language }}</div>
                <div>
                    <span>Voto: </span>
                    <i 
                        v-for="star in roundVote(item.vote_average)" 
                        :key="item.id+star"
                        class="fas fa-star"> 
                    </i>
                    <i
                        v-for="(emptystar, index) in (5-roundVote(item.vote_average))" 
                        :key="index"
                        class="far fa-star"> 
                    </i> 
                </div>
                <div>
                    <span>Overview:</span>
                    {{ getOverview().substr(0, 300) }}...
                </div>
            </div>
            
        </div>
        
            
            <!-- <img 
            class="flag" 
            v-if="this.item.original_language == 'it' " 
            src="../assets/images/it.png" alt="flag">
            <img 
            class="flag" 
            v-else-if="this.item.original_language == 'en' " 
            src="../assets/images/en.png" alt="flag">
            <li 
            v-else> {{ item.original_language }} </li> -->
            
    </div>
</template>

<script>
export default {
    name: "Film",
    props: [ "item" ],

    data: function () {
        return {
            avaibleFlags: [ "it", "en" ]
        }
    },

    methods: {
        getImage: function () {
            if (this.item.poster_path) {
                // Poster è presente
                return "https://image.tmdb.org/t/p/w342" + this.item.poster_path;
            } else {
                // Poster non presente
                return "https://yt3.ggpht.com/ytc/AAUvwnhwzaiFlrl0XXAxA6aKhMQSGyAqM--Ez5cbf51poQ=s900-c-k-c0x00ffffff-no-rj"
            }
        },

        getOverview: function () {
            if (this.item.overview) {
                return this.item.overview;
            } else {
                return "La descrizione di questo film al momento non è disponibile"
            }
        },

        roundVote: function (vote) {
            var number = (vote / 2);
            var rounded = Math.round(number);
            return rounded;
        }
    }
            
            

}
</script>

<style lang="scss" scoped>
    
    .card {
        width: 300px;
        height: 400px;
        background-color: grey;
        border: 1px solid white;
        margin: 20px;
        overflow: hidden;
        transition: all 0.5s;

        .info {
            display: none;
        }
    }

    .card:hover {
        background-color: black;
        padding: 40px 10px 0 10px;
        transform: scale(1.1);

        .info {
            display: block;
            color: white;

            i {
                font-size: 18px;
                color: yellow;
            }
        }

        span {
            font-weight: bold;
        }

        img {
            display: none;
        }
    }
        

    img {
        width: 300px;
        height: 400px;
    }
    
    .flag {
        height: 20px;
        width: 30px;
    }
</style>
            
        
            
    

                
                


    