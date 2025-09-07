
<template>

    <main class="py-8 flex flex-col gap-4 items-center">

        <h1 class="text-3xl">Hello world TailwindCSS3!</h1>

        <form class="flex flex-row join" @submit.prevent="greet">
            <input class="input join-item" v-model="name" placeholder="Enter name..." />
            <button type="submit" class="btn btn-primary join-item">Greet</button>
        </form>
        <p>{{ greetMsg }}</p>
        <div ref="editor" class="editor"></div>
    </main>
</template>


<style>

:root {
    color: #0f0f0f;
    background-color: #f6f6f6;
}

.editor {
    width: 100vw;
    height: 100vh;
}
@media (prefers-color-scheme: dark) {
    :root {
        color: #f6f6f6;
        background-color: #2f2f2f;
    }
}

</style>


<script setup lang="ts">

import { ref, onMounted } from 'vue';
import { invoke } from '@tauri-apps/api/core';
import { createEditor } from './editor';

const greetMsg = ref('');
const name = ref('');
const editor = ref(null);

async function greet() {
    greetMsg.value = await invoke('greet', { name: name.value });
}

onMounted(() => {
    createEditor(editor.value);
});

</script>
