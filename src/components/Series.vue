<template>
    <div class="text-center pb-4 card">
        <div><img :src="getImage()"></div>
        <div>{{ item.name }}</div>
        <div>{{ item.original_name }}</div>
        <div v-if="availableFlags.includes(item.original_language)">
            <img 
            class="flag"
            :src="require(`../assets/images/${item.original_language}.png`)" 
            :alt="`bandiera ${item.original_language}`"
            >
        </div>
        <div v-else> {{ item.original_language }}</div>
        <div>
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
        
    </div>
</template>

<script>
export default {
    name: "Series",
    props: [ "item" ],

    data: function () {
        return {
            availableFlags: [ "it", "en" ],
        }
    },

    methods: {
        getImage: function () {
            
            if (this.item.poster_path) {
                // Poster è presente
                return "https://image.tmdb.org/t/p/w342" + this.item.poster_path;
            } else {
                // Poster non presente
                return "https://image.shutterstock.com/image-vector/empty-placeholder-image-icon-design-260nw-1366372628.jpg"
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
        width: 400px;
        background-color: grey;
        border: none;
    }

    img {
        width: 200px;
        height: 250px;
    }

    .flag {
        height: 20px;
        width: 30px;
    }

    
</style>

                
                
