<script setup>
import { Field, Form, ErrorMessage } from 'vee-validate'
import * as yup from 'yup'

const schema = yup.object({
    email: yup.string().email().required(),
    name: yup.string().required(),
    privacy: yup.boolean().oneOf([true], 'You must accept the privacy policy').required(),
})

function onSubmit(values) {
    console.log(JSON.stringify(values, null, 2))
}
</script>

<template>
    <div class="wrapper">
        <h3>Form validation with VeeValidate</h3>
        <Form @submit="onSubmit" :validation-schema="schema">
            <label for="name" class="visually-hidden">Name</label>
            <Field
                type="text"
                name="name"
                id="name"
                placeholder="Enter name" />
            <ErrorMessage name="name" />

            <label for="email" class="visually-hidden">Email</label>
            <Field
                type="email"
                name="email"
                id="email"
                placeholder="Enter email"
            />
            <ErrorMessage name="email" />

            <Field
                v-slot="{ field }"
                type="checkbox"
                name="privacy"
                id="privacy"
                :value="true"
                :unchecked-value="false"
            >
                <label for="privacy" class="checkbox-label">
                    <input type="checkbox" name="privacy" id="privacy" v-bind="field" :value="true" />
                    I agree to the privacy
                </label>
            </Field>
            <ErrorMessage name="privacy" />

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

input,
button {
    width: 200px;
}

input[type="checkbox"] {
    width: 15px;
}

.checkbox-label {
    width: 200px;
    display: flex;
    gap: 10px;
    align-items: center;
    white-space: nowrap;
}

span[role='alert'] {
    margin-top: -10px;
    font-weight: bold;
    font-size: 12px;
    color: #d22b2b;
}

.checkbox-wrapper span[role='alert'] {
    margin-top: 0;
}
</style>
