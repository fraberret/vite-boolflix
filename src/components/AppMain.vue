<script>

import Card from './Card.vue'
export default {
    name: 'AppMain',
    components: {
        Card,
    },
    props: {
        contents: Array
    }

}
</script>

<template>
    <div class="container pt-4">
        <div class="row g-3">
            <Card v-for="contents in contents" :contents="contents" />
        </div>
    </div>
</template>

<style lang="scss" scoped></style>