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
    <main>
        <div class="container pt-4">
            <div class="row g-3">
                <Card v-for="contents in contents" :contents="contents" />
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped></style>