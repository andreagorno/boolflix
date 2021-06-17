<template>
    <div class="home">
        <div class="powered">
            powered by Andrea Gorno
        </div>
        <button>
            <img src="../assets/images/netflix_logo.png" alt="">
        </button>
    </div>
</template>

<script>
export default {
    name: "Intro",
    // data: function () {
    //     return {

    //     }
    // }
}
</script>

<style lang="scss" scoped>
    .home {
        width: 100%;
        height: 100vh;
        background-color: black;
        display: flex;
        justify-content: center;
        align-items: center;

        button {
            background-color: black;
            border-radius: 5px;
            border: 2px solid black;

            img {
                height: 100px;
                animation: pulse 2s linear infinite alternate;
            }
        }
    }
    @keyframes pulse {
        from {
            transform: scale(1);
        }
        to {
            transform: scale(1.5);
        }
    }
    
    .powered {
        position: absolute;
        top: 5px;
        right: 5px;
        color: red;
        font-size: 16px;
    }
</style>