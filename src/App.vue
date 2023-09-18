<script setup>
import Header from './components/Header.vue';
import List from './components/List.vue';

import { provide, ref, computed } from 'vue';

/**
 * Props
 */

// Create a ref for the selected emojis, which is an array of arrays (one array per subconcept)
const selectedEmojis = ref([[]]);


/**
 * Methods
 */

// Add an emoji to the selectedEmojis array
const addEmoji = (emoji) => {
  //Add the emoji to the last array of the selectedEmojis array
  selectedEmojis.value[selectedEmojis.value.length - 1].push(emoji);
};

// Method that adds a new subconcept to the selectedEmojis array
const addSubConcept = () => {
  // Add a new empty array to the selectedEmojis array
  selectedEmojis.value.push([]);
};

// Remove the last emoji from the last array of the selectedEmojis array
const removeLastEmoji = () => {
  // If the last array is empty, remove it
  if (selectedEmojis.value[selectedEmojis.value.length - 1].length === 0) {
    selectedEmojis.value.pop();
  }
  else {

    selectedEmojis.value[selectedEmojis.value.length - 1].pop();
  }
};

/**
 * Computed
 */

// Check if the last array of the selectedEmojis array is empty
const isLastArrayEmpty = computed(() => {
  return selectedEmojis.value[selectedEmojis.value.length - 1].length === 0;
});

// Check if there are any emojis selected
const isAnyEmojiSelected = computed(() => {

  // Check if all the subarrays are empty
  for (let i = 0; i < selectedEmojis.value.length; i++) {
    if (selectedEmojis.value[i].length !== 0) {
      return true;
    }
  }

  return false;
});

// Check if there are many subconcepts
const areManySubConcepts = computed(() => {

  return selectedEmojis.value.length > 1;

});

// Method that transforms the selectedEmojis array into a string
const stringifiedConcept = computed(() => {
  // Create an empty string
  let string = '';

  // Loop through the selectedEmojis array
  for (let i = 0; i < selectedEmojis.value.length; i++) {
    
    // If it's not the first subarray, add a sign before the subconcept
    if (i !== 0) {
      string += '┗ ';
    }
    
    // Loop through the subarrays
    for (let j = 0; j < selectedEmojis.value[i].length; j++) {
      // Add the emoji to the string
      string += selectedEmojis.value[i][j].emoji;
    }
    // Line break
    string += '\n\r';
  }

  // Remove the last space from the string
  string = string.slice(0, -1);

  // Return the string
  return string;
});



// Check if the selectedEmojis array contains exactly one emoji
const isOneEmojiSelected = computed(() => {
  return selectedEmojis.value[0].length === 1 && selectedEmojis.value.length === 1;
});

// Check if the selectedEmojis array contains at least two emojis or subconcepts
const isTwoOrMoreSelected = computed(() => {
  return selectedEmojis.value[0].length >= 2 || selectedEmojis.value.length >= 2;
});

// Provide the selectedEmojis array to the components
provide('selectedEmojis', {
  selectedEmojis,
  isLastArrayEmpty,
  isAnyEmojiSelected,
  stringifiedConcept,
  areManySubConcepts,
  isOneEmojiSelected,
  isTwoOrMoreSelected,
  removeLastEmoji,
  addSubConcept
});

</script>

<template>
  <div class="wrapper">
    <Header />
    <List @selected-emoji="addEmoji"></List>
  </div>
</template>


<style scoped>

@media screen and (min-width: 1024px) {
  .wrapper {
    display: flex;
    justify-content: stretch;
    align-items: TOP;
    height: 100vh;
  }
}

</style>
