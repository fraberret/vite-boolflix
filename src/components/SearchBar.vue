<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: ''
        }
    },
    methods: {
        searchFilms() {
            console.log(this.searchText);
        }
    }
}
</script>

<template>
    <input type="text" v-model="searchText">
    <button @click="searchFilms">Search</button>

</template>


<style lang="scss" scoped></style>