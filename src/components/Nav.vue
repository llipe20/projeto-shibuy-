<template>
    <nav>
        <router-link to="/" id="box-logo">
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <router-link to="/">Home</router-link> |
        <router-link to="/pedidos">Pedidos</router-link>
    </nav>
</template>
<script>
export default {
    name : "Nav",
    props : ["logo", "alt"]
}
</script>

<style scoped>
nav {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    background-color: black;
    padding: 20px 30px;
    height: auto;
    width: 100vw;
}

#box-logo {
    margin: auto;
    margin-left: 0;
}

#logo {
    width: 40px;
    height: 40px;
}

nav a {
    color: yellow;
    font: normal 1.2em 'Arial';
    text-decoration: none;
    transition: .3s;
    margin: 1px 15px;
}

nav a:hover {
    color: white;
}
</style>