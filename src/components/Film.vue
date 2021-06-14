<template>
    <div class="text-center pb-4">
        <ul>
            <li>{{ item.title }}</li>
            <li> {{ item.original_title }} </li>
            <li> {{ item.original_language }} </li>
            <li> {{ item.vote_average }} </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Film",
    props: [ "item" ]
}
</script>

<style lang="scss" scoped>
    ul {
        list-style: none;
    }
</style>