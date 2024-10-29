<script setup>
import { ref } from 'vue'

const newPost = ref({
    title: '',
    author: '',
    content: '',
    label: '',
    image: null,
})
const posts = ref([])
const labelOptions = ['Technology', 'Education', 'Business']

const submitForm = () => {
    if (
        newPost.value.title &&
        newPost.value.author &&
        newPost.value.content &&
        newPost.value.label
    ) {posts.value.push({ ...newPost.value })

        // Reset
        newPost.value = {
            title: '',
            author: '',
            content: '',
            label: '',
            image: null,
        }
    }
}

const handleFileChange = (event) => {
    const file = event.target.files[0]
    if (file) {
        newPost.value.image = URL.createObjectURL(file)
    }
}
</script>

<template>
    <div class="blog-post-form">
        <h3>Blog posts</h3>
        <form class="form" @submit.prevent="submitForm">
            <div>
                <label for="title" class="visually-hidden"> Title </label>
                <input
                    v-model="newPost.title"
                    type="text"
                    id="title"
                    placeholder="Enter post title"
                    required
                />
            </div>
            <div>
                <label for="author" class="visually-hidden">
                    Author Name:
                </label>
                <input
                    v-model="newPost.author"
                    type="text"
                    id="author"
                    placeholder="Enter author name"
                    required
                />
            </div>
            <div>
                <label for="content" class="visually-hidden"> Content </label>
                <textarea
                    v-model="newPost.content"
                    id="content"
                    rows="5"
                    placeholder="Enter post content"
                    required
                ></textarea>
            </div>
            <div>
                <label for="image" class="file-upload">Choose image</label>
                <input
                    type="file"
                    id="image"
                    accept="image/*"
                    @change="handleFileChange"
                />
            </div>
            <div>
                <label for="label" class="visually-hidden"> Post label </label>
                <select v-model="newPost.label" id="label" required>
                    <option disabled value="">Select a label</option>
                    <option
                        v-for="option in labelOptions"
                        :key="option"
                        :value="option"
                    >
                        {{ option }}
                    </option>
                </select>
            </div>
            <button type="submit">Add Post</button>
        </form>
        <div v-if="posts.length > 0" class="blog-list">
            <h3>All blog posts</h3>
            <ul>
                <li v-for="(post, index) in posts" :key="index">
                    <h4>{{ post.title }}</h4>
                    <img class="post-img" v-if="post.image" :src="post.image" alt="Post Image" />
                    <p><strong>Author:</strong> {{ post.author }}</p>
                    <p>{{ post.content }}</p>
                    <p><strong>Label:</strong> {{ post.label }}</p>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
.blog-post-form {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-block: 30px;
}

.blog-list {
    margin-top: 30px;
}

.blog-list ul {
    list-style-type: none;
    padding: 0;
}

.blog-list li {
    border-bottom: 1px solid #ddd;
    padding: 15px 0;
}
</style>
