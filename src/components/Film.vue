<template>
    <div class="text-center pb-4">
        <ul>
            <li> {{ item.title }} </li>
            <li> {{ item.original_title }} </li>
            <li v-show="this.item.original_language != 'it' && this.item.original_language != 'en' "> {{ item.original_language }} </li>
            <img v-show="this.item.original_language == 'it' " src="../assets/images/it.png" alt="flag">
            <img v-show="this.item.original_language == 'en' " src="../assets/images/en.png" alt="flag">
            <li> {{ item.vote_average }} </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Film",
    props: [ "item" ],

    methods: {
        // getFlags: function () {
        //    if (this.item.original_language == "it") {
               
        //    } 
        // }
    }
}
</script>

<style lang="scss" scoped>
    ul {
        list-style: none;
    }

    img {
        height: 10px;
    }
</style>