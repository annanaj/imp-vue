<script setup>
import IntroMessage from '@/components/IntroMessage.vue'
import CounterBox from '@/components/CounterBox.vue'
import BlogPosts from '@/components/BlogPosts.vue'
import FormValidation from '@/components/FormValidation.vue'
</script>

<template>
    <div class="main-container">
        <IntroMessage msg="Vue sandbox" />
        <FormValidation />
        <BlogPosts />
        <CounterBox />
    </div>
</template>
