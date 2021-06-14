<template>
    <header>
        <button 
        @click.prevent="$emit('performSearch', searchText)"
        >Submit</button>
        <input 
        type="text" 
        placeholder="Cosa stai Cercando?"
        v-model.trim="searchText"
        >
    </header>
</template>

<script>
export default {
    name: "Search",

    data: function () {
        return {
            searchText: ""
        }
    },

    computed: {
        // uppercaseText: function () {
        //     return this.searchText.toUpperCase();
        // }
    },

    methods: {
        search: function () {
            console.log("Ricerca");
        },
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
</style>