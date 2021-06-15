<template>
    <div class="text-center pb-4">
        <ul>
            <li>
                <img :src="getImage()">
            </li>
            <li> {{ item.name }} </li>
            <li> {{ item.original_name }} </li>
            <li v-show="this.item.original_language != 'it' && this.item.original_language != 'en' "> {{ item.original_language }} </li>
            <img class="flag" v-show="this.item.original_language == 'it' " src="../assets/images/it.png" alt="flag">
            <img class="flag" v-show="this.item.original_language == 'en' " src="../assets/images/en.png" alt="flag">
            <li> {{ item.vote_average }} </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Series",
    props: [ "item" ],

    methods: {
        getImage: function () {
            return "https://image.tmdb.org/t/p/w342" + this.item.poster_path;
        }
    }
}
            
</script>

<style lang="scss" scoped>
    div {
        display: flex;
        justify-content: center;
    }
    ul {
        list-style: none;
        padding: 0;

        li:first-child {
            text-align: center;
            
            img {
                width: 100px;
                height: 150px;
            }
        }
            

                
                

        .flag {
            height: 10px;
        }

    }

    
</style>