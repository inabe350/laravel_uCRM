<script setup>
import { reactive } from 'vue';
import { Inertia } from '@inertiajs/inertia';

defineProps({
    errors: Object
})

const form = reactive({
    title: null,
    content: null
})

const submitFunction = () => {
    Inertia.post('/inertia', form)
}
</script>

<template>
    <form @submit.prevent="submitFunction">
        <input type="text" name="title" v-model="form.title"><br>
        <InputError v-if="errors.title">{{ errors.title }}</InputError><br>
        <input type="text" name="content" v-model="form.content"><br>
        <InputError v-if="errors.content">{{ errors.content }}</InputError><br>
        <button>送信</button>
    </form>
</template>