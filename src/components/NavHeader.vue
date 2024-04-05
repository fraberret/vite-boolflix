<template>
    <nav>
        <ul>
            <li>Home</li>
            <li>Serie Tv</li>
            <li>Film</li>
        </ul>
    </nav>
</template>

<script>
export default {
    name: 'NavHeader'
}
</script>

<style>
ul {
    color: white;
    display: flex;
    gap: 2rem;
    list-style: none;
    align-items: center;
    margin: 0;
}

li:hover {
    cursor: pointer;
    color: rgb(157, 155, 155);
    transition: .5s;


}
</style>