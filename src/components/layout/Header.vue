<template>
    <header class="header">
        <h1>Todo List</h1>
        <div class="nav">
            <router-link to="/">Home</router-link>
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        background: #333;
        color: white;
        text-align: center;
        padding: 10px;
        margin-bottom: 1rem;
    }

    .header a {
        color: #FFF;
        display: inline-block;
        padding-right: 5px;
        text-decoration: none;
    }
</style>