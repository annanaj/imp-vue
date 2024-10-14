<script setup>
import { Field, Form, ErrorMessage } from 'vee-validate';
import * as yup from 'yup';

const schema = yup.object({
    email: yup.string().email().required(),
    name: yup.string().required(),
});

function onSubmit(values) {
    alert(JSON.stringify(values, null, 2));
}
</script>

<template>
    <div class="wrapper">
        <h3>Form validation with VeeValidate</h3>
        <Form @submit="onSubmit" :validation-schema="schema">
            <label for="name" class="visually-hidden">Name</label>
            <Field type="text" name="name" />
            <ErrorMessage name="name" />

            <label for="email" class="visually-hidden">Email</label>
            <Field type="email" name="email" />
            <ErrorMessage name="email" />
            <button>Sign up</button>
        </Form>
    </div>
</template>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 30px;
}

input, button {
    width: 200px;
}

span[role=alert] {
    margin-top: -10px;
    font-weight: bold;
    font-size: 12px;
    color: #D22B2B;
}
</style>