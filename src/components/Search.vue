<template>
    <header>
        
        <button 
        @click.prevent="$emit('performSearch', searchText)">
            <i class="fas fa-search"></i>
        </button>
        <input 
        type="text" 
        placeholder="Cosa stai Cercando?"
        v-model.trim="searchText"
        >
        <div>
            <img 
            src="../assets/images/netflix_logo.png" 
            alt="netflix_logo">
        </div>

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

    methods: {
        search: function () {
            console.log("Ricerca");
        },
    }
}
</script>

<style lang="scss" scoped>
    header {
        position: fixed;
        display: flex;
        flex-direction: row-reverse;
        align-items: center;
        width: 100%;
        height: 10vh;
        background-color: black;
        z-index: 10;

        input,
        button {
            padding: 5px;
            
        }

        button {
            margin-right: 30px;
            background-color: black;
            border: none;

            i {
                font-size: 20px;
                color: white;
            }
        }

        input {
            width: 300px;
            margin-right: 5px;
            border: 2px solid white;
            background-color: rgba($color: #000000, $alpha: 0.7);
            color: white;
            border-radius: 5px;
        }
        ::placeholder {
            color: grey;
            opacity: 1; /* Firefox */
        }

        div {
            flex-grow: 1;
            margin-left: 20px;
        }
    }
</style>