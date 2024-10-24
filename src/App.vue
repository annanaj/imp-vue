<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <header class="header">
        <div class="logo">
            <img
                alt="Vue logo"
                class="logo"
                src="@/assets/logo.svg"
                width="30"
                height="30"
            />
        </div>
        <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
    </header>
    <RouterView />
</template>

<style scoped>
.header {
    position: fixed;
    top: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 1rem;
    background-color: #edf9f3;
    border-bottom: 1px solid #c2e9d7;
}

nav {
    display: flex;
}

nav a.router-link-exact-active {
    color: var(--color-text);
}

nav a.router-link-exact-active:hover {
    background-color: transparent;
}

nav a {
    display: inline-block;
    padding: 0 1rem;
    border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
    border: 0;
}

.main-container {
    display: flex;
    margin-inline: auto;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    width: 100%;
    max-width: 700px;
    margin-block: 100px;
}

.main-container > * {
    width: 90%;
    border-bottom: 1px dashed #e6e6e6;
}

.main-container > *:first-child {
    border-bottom: none;
}
</style>
