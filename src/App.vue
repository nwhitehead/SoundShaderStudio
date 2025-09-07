
<template>

    <main class="py-8 flex flex-col gap-4 items-center">

        <h1 class="text-3xl font-bold underline">Hello world TailwindCSS3!</h1>

        <form class="flex flex-row" @submit.prevent="greet">
            <input id="greet-input" v-model="name" placeholder="Enter name..." />
            <button type="submit">Greet</button>
        </form>
        <p>{{ greetMsg }}</p>
    </main>
</template>


<style>

:root {
    color: #0f0f0f;
    background-color: #f6f6f6;
}

input,
button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    color: #0f0f0f;
    background-color: #ffffff;
    transition: border-color 0.25s;
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
}

button {
    cursor: pointer;
}

button:hover {
    border-color: #396cd8;
}
button:active {
    border-color: #396cd8;
    background-color: #e8e8e8;
}

input,
button {
    outline: none;
}

#greet-input {
    margin-right: 5px;
}

@media (prefers-color-scheme: dark) {
    :root {
        color: #f6f6f6;
        background-color: #2f2f2f;
    }

    a:hover {
        color: #24c8db;
    }

    input,
    button {
        color: #ffffff;
        background-color: #0f0f0f98;
    }
    button:active {
        background-color: #0f0f0f69;
    }
}

</style>


<script setup lang="ts">

import { ref } from 'vue';
import { invoke } from '@tauri-apps/api/core';

const greetMsg = ref('');
const name = ref('');

async function greet() {
    greetMsg.value = await invoke('greet', { name: name.value });
}

</script>
