<template>
    <main>
        <input type="text" class="searchbar" v-model="searchInput" placeholder="Rechercher un emoji">

        <ul>
            <li class="emoji" @click="$emit('selectedEmoji', emoji)" v-for="emoji in filteredEmojis" :key="emoji.name">
                <span class="symbol">{{ emoji.emoji }}</span>
                <span class="meaning">{{ emoji.meaning }}</span>
            </li>
        </ul>
    </main>
</template>

<script setup>

import { ref, computed } from 'vue';
//Import the list of emojis from the data file
import emojis from '../data/emojis.js';

// Ref for the search input value
const searchInput = ref('');

// Computed for the filtered emojis
const filteredEmojis = computed(() => {
    // If the search input is empty, return the full list of emojis
    if (searchInput.value === '') {
        return emojis;
    }
    // Else, return the filtered list of emojis by searching through the name, meaning and keywords properties
    else {
        return emojis.filter(emoji => {
            return emoji.name.toLowerCase().includes(searchInput.value.toLowerCase()) || emoji.meaning.toLowerCase().includes(searchInput.value.toLowerCase()) || emoji.keywords?.toLowerCase().includes(searchInput.value.toLowerCase());
        });
    }
   
});



</script>

<style scoped>

    main {
        padding: 1rem;
        overflow-y: scroll;
        flex: 1;
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
    .searchbar {
        border: 2px solid var(--grid-dark);
        border-radius: 3px;
        color: var(--grid-dark);
        width: 100%;
        padding: 1rem;
        margin-bottom: 2rem;
        outline: none;
        font-size: 1.1rem;
    }

</style>