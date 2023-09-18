<template>
    <main>
        <ul>
            <li class="emoji" @click="$emit('selectedEmoji', emoji)" v-for="emoji in emojis" :key="emoji.name">
                <span class="symbol">{{ emoji.emoji }}</span>
                <span class="meaning">{{ emoji.meaning }}</span>
            </li>
        </ul>
    </main>
</template>

<script setup>
//Import the list of emojis from the data file
import emojis from '../data/emojis.js';



</script>

<style scoped>

    main {
        padding: 1rem;
    }

    .emoji {
        display: flex;
        align-items: center;
        margin-bottom: 1rem;
        font-size: 2rem;
        cursor: pointer;
    }

    .symbol {
        font-size: 3rem;
        margin-right: 1rem;
        line-height: 1.2;
    }

</style>