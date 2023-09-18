<template>
    <Transition name="fade">
        <button class="button add"  :class="{shrinked: areManySubConcepts}" @click="addSubConcept" :disabled="isLastArrayEmpty" v-if="isAnyEmojiSelected"><i class="gg-add"></i> 
                <span class="label">
                    Ajouter un sous-concept
                </span>
        </button>
    </Transition>
    <Transition name="fade">
        <button class="button" @click="removeLastEmoji" v-if="isAnyEmojiSelected">
            <i class="gg-remove"></i>
        </button>
    </Transition>
</template>

<script setup>
    import { inject } from 'vue';

    // Inject the selectedEmojis array, and array tools from the App.vue component
    const { 
    isLastArrayEmpty, 
    isAnyEmojiSelected, 
    addSubConcept, 
    areManySubConcepts,
    removeLastEmoji
    } = inject('selectedEmojis');

</script>

<style scoped>
 button {
        margin-right: 1rem;
        width: 3.5rem;
    }
    .button.add {
        display: flex;
        align-items: center;
        justify-content: center;
        line-height: 1;
        overflow: hidden;
        transition: all 0.2s ease;
        width: 16rem;

    }
    .gg-add {
        top: -2px;
        position: relative;
    }
    
    .label {
        margin-left: 0.5rem;
        transition: all .5s ease;
        opacity: 1;
        white-space: nowrap;

    }

    .shrinked .label {
        opacity: 0;
        transform: translateX(-20px);
        display: none;
    }
    .shrinked.add {
        width: 3.5rem;
    }


</style>