<script setup>
import { defineProps } from 'vue'

// directly define the props
const { msg } = defineProps({
    msg: String,
})
</script>

<template>
    <div>
        <h1>{{ msg }}</h1>
    </div>
</template>

<style scoped>
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
