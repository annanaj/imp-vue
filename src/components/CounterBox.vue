<script setup>
import { ref } from 'vue'

const num1 = ref(1)
const num2 = ref(1)
const name = ref('')
</script>

<template>
    <div class="wrapper">
        <h3>basic v-model.number</h3>
        <div class="counter">
            <input v-model.number="num1" type="number" />
            <span>+</span>
            <input v-model.number="num2" type="number" />
            <span>=</span>
            <span>{{ num1 + num2 }}</span>
        </div>
    </div>
</template>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
}

.counter {
    padding-bottom: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 5px;
}

input {
    width: 50px;
}
</style>
