<template>
    <header class="header">
        <h1>TodoList</h1>
    <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
    </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style >
    .header {
        background: rgb(236, 144, 144);
        color: #fff;
        /* margin-top: 10px; */
        text-align: center;
        padding: 10px;
    }
    .header h1 {
        margin-top: 10px;
    }
    .header a {
        color: #fff;
        padding-right: 5px;
        text-decoration: none;
    }
</style>