<template>
        <!-- <h2>Mon concept</h2> -->
        <div class="concept-wrapper">
            <div class="selected-emojis">
                <pre v-if="isAnyEmojiSelected">{{ stringifiedConcept }}</pre>
                <p class="info" v-if="!isTwoOrMoreSelected">
                    <Transition name="fade">
                        <template v-if="!isAnyEmojiSelected">Choisissez un premier emoji représentant le mot à faire deviner.</template>
                    </Transition>
                    <Transition name="fade">
                        <template v-if="isOneEmojiSelected">Maintenant, vous pouvez ajouter des emojis pour préciser le concept principal, ou ajouter un sous-concept !</template>
                    </Transition>
                </p>
            </div>
            <div class="selected-emojis__buttons">
                <Buttons />
            </div>
            <div class="copy-wrapper">
                <CopyButton />
            </div>
        </div>
</template>

<script setup>
import { inject } from 'vue';
import Buttons from './Buttons.vue';
import CopyButton from './CopyButton.vue';

   // Inject the selectedEmojis array, and array tools from the App.vue component
   const { 
    isAnyEmojiSelected, 
    stringifiedConcept,
    isOneEmojiSelected, 
    isTwoOrMoreSelected,
    stringifiedConceptWithUrl,
    } = inject('selectedEmojis');
    
    

</script>

<style scoped lang="scss">

   
    .selected-emojis__buttons {
        display: flex;
        justify-content: start;
        margin-top: 1rem;
    }

    .info {
        line-height: 1;
        background: rgb(249, 249, 215);
        padding: 1rem;
        border-radius: 3px;
    }

    .selected-emojis pre {
        font-size: 2rem;
    }

    .copy-wrapper {
        display: flex;
        justify-content: center;
        margin-top: 1rem;
    }
  
    
</style>