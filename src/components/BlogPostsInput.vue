<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue';

// Define props to receive data from the parent
const props = defineProps({
    inputData: {
        type: String,
        required: true
    }
});

// Define emits to send events back to the parent
const emit = defineEmits(['updateData']);

// Local reactive state for the input field
const localData = ref(props.inputData);

// Watch for changes to inputData (prop) and sync it with localData
watch(() => props.inputData, (newVal) => {
    localData.value = newVal;
});

// Emit the updated data back to the parent when the button is clicked
const emitUpdatedData = () => {
    emit('updateData', localData.value);
};
</script>

<template>
    <div>
        <slot name="header"></slot> <!-- Named Slot for Header -->

        <div>
            <p>{{ inputData }}</p>
            <input v-model="localData" type="text" />
            <button @click="emitUpdatedData">Update Data</button>
        </div>

        <slot name="footer"></slot> <!-- Named Slot for Footer -->
    </div>
</template>
