<template>
<div class="links">
    <nuxt-link to="/" class="link">Home</nuxt-link>
    <nuxt-link to="/tasks" class="link">Tasks</nuxt-link>
</div>
</template>
<style scoped>
    *{
        padding: 0;
        margin: 0;
    }
    .links{
        display: flex;
        justify-content:center;
        width: 100vw;
        margin: 0;
        padding: 0;
    }
    .link{
        padding: 10px;
        color: rgb(245, 122, 7);
        font-size: 25px;
        text-decoration: none;
        margin: 20px 20px;
    }
</style>