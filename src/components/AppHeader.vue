<script>
import SearchBar from './SearchBar.vue';
import AppLogo from './AppLogo.vue';
import NavHeader from './NavHeader.vue';

export default {
    name: 'AppHeader',
    components: {
        SearchBar,
        AppLogo,
        NavHeader
    },
    methods: {
        performSearch(searchText) {
            this.$emit('search', searchText);
        }
    }

}
</script>

<template>
    <header>
        <div class="l">
            <AppLogo />
            <NavHeader />
            <SearchBar @search="performSearch" />

        </div>
    </header>
</template>


<style>
.l {
    width: 100%;
    display: flex;
    position: relative;
    align-items: center;
}
</style>