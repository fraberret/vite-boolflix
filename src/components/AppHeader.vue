<script>
import SearchBar from './SearchBar.vue';
import AppLogo from './AppLogo.vue';

export default {
    name: 'AppHeader',
    components: {
        SearchBar,
        AppLogo
    },
    methods: {
        performSearch(searchText) {
            this.$emit('search', searchText);
        }
    }

}
</script>

<template>
    <div class="header">
        <AppLogo />
        <SearchBar @search="performSearch" />
    </div>
</template>


<style></style>