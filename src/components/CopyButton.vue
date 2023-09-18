<template>
    <button class="copy" :class="buttonClass" @click="copyConcept" :disabled="!isAnyEmojiSelected">
        <div class="message">
            Copier le Concept
        </div>
        <div class="success">
            Copié !
        </div>
    </button>
</template>

<script setup>

import { inject, ref } from 'vue';
import { useClipboard } from '@vueuse/core'


// Inject the  array tools from the App.vue component
const { 
    isAnyEmojiSelected, 
    stringifiedConceptWithUrl,
    } = inject('selectedEmojis');

const { copy } = useClipboard({stringifiedConceptWithUrl})

const buttonClass = ref('');

// Method that copies the concept to the clipboard and add a class to the button, then remove it after 1 second
const copyConcept = () => {
    copy(stringifiedConceptWithUrl.value);
    buttonClass.value = 'copied';
    setTimeout(() => {
        buttonClass.value = '';
    }, 2000);
};

</script>

<style scoped lang="scss">
.copy {
        background: #1e88e5;
        color: white;
        padding: 0.5rem 1rem;
        overflow: hidden;
        position: relative;
}

.success {
    position: absolute;
    inset: 0;
    transform: translate(0, 100%);
    display: flex;
    align-items: center;
    justify-content: center;
}
.copied {
    background: rgb(46, 148, 46);
    .success {
        transform: translate(0, 0);
    }
    .message {
        transform: translate(0, -100%);
    }
}

</style>