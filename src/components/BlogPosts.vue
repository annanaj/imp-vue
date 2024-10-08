<script>
import { ref } from 'vue';

export default {
    setup() {
        // Reactive data for new blog post
        const newPost = ref({
            title: '',
            author: '',
            content: '',
            label: '',
        });

        // Reactive list of blog posts
        const posts = ref([]);

        // Predefined label options for the select input
        const labelOptions = ['Technology', 'Education', 'Business'];

        // Function to add the new post to the posts array
        const submitForm = () => {
            if (newPost.value.title && newPost.value.author && newPost.value.content && newPost.value.label) {
                // Add the new post to the list of posts
                posts.value.push({ ...newPost.value });

                // Reset form fields after submission
                newPost.value = {
                    title: '',
                    author: '',
                    content: '',
                    label: '',
                };
            }
        };

        // Return everything to be used in the template
        return {
            newPost,
            posts,
            labelOptions,
            submitForm,
        };
    },
};
</script>

<template>
    <div class="blog-post-form">
        <h3>Blog posts</h3>
        <form class="form" @submit.prevent="submitForm">
            <div>
                <label
                    for="title"
                    class="visually-hidden"
                >
                    Title
                </label>
                <input
                    v-model="newPost.title"
                    type="text"
                    id="title"
                    placeholder="Enter post title"
                    required
                />
            </div>
            <div>
                <label
                    for="author"
                    class="visually-hidden"
                >
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
                <label
                    for="content"
                    class="visually-hidden"
                >
                    Content
                </label>
                <textarea
                    v-model="newPost.content"
                    id="content"
                    rows="5"
                    placeholder="Enter post content"
                    required
                ></textarea>
            </div>
            <div>
                <label
                    for="label"
                    class="visually-hidden"
                >
                    Post label
                </label>
                <select
                    v-model="newPost.label"
                    id="label"
                    required
                >
                    <option disabled value="">Select a label</option>
                    <option v-for="option in labelOptions" :key="option" :value="option">
                        {{ option }}
                    </option>
                </select>
            </div>
            <button type="submit">Add Post</button>
        </form>
        <div v-if="posts.length > 0" class="blog-list">
            <h2>All blog posts</h2>
            <ul>
                <li v-for="(post, index) in posts" :key="index">
                    <h3>{{ post.title }}</h3>
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

.form {
    max-width: 300px;
}

button {
    padding: 10px;
    font-size: 16px;
    background-color: #42b883;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #3daa79;
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