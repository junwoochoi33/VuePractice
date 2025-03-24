<template>
    <nav class="navbar">
        <a href="#none">Home</a>
        <a href="#none">Bulletin Board</a>
        <a href="#none">About</a>
    </nav>

</template>

<script>
    export default {
        name: 'NavbarComponent'
    }

</script>

<style>
    .navbar {
        background: #000;
        padding: 20px;
        text-align: center;
    }

    .navbar a {
        color: #fff;
        text-decoration: none;
        padding: 1em;
    }

</style>