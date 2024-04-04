<script>

export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: '',
        }
    },

    methods: {
        search() {

            this.$emit('search', this.searchText);
        }
    }

}
</script>

<template>
    <div class="search_bar">
        <input type="text" v-model="searchText" @keyup.enter="search">
        <button @click="search">Search</button>
    </div>
</template>


<style lang="scss" scoped></style>