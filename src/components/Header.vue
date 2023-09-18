<template>
    <Modal  @close="toggleModal" v-if="modal"/>
    <header>
        <div class="wrapper">
            <h1>Emoji Concept <span class="mark" @click="toggleModal" >?</span></h1>
            <SelectedEmojis />
        </div>
    </header>
</template>

<script setup>
    import { ref } from 'vue';
    import Modal from './Modal.vue';
    import SelectedEmojis from './SelectedEmojis.vue';

    const modal = ref(false);

    const toggleModal = () => {
        modal.value = !modal.value;
    };

</script>

<style>

h1 {
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}

header {
    background-color: #f5f5f5;
    padding: 1rem;
    width: 100%;
}
.mark {
    color: #f5f5f5;
    background-color: var(--grid-dark);
    border-radius: 50%;
    width: 2rem;
    height: 2rem;
    display: inline-block;
    line-height: 2.25rem;
    font-size: 2.5rem;
    margin-left: .5rem;
    position: relative;
    top: -.25rem;
    cursor: pointer;
}


@media screen and (min-width: 1024px) {
    header {
        width: 50%;
        height: 100%;
        padding: 1rem 3rem;
    }
}

@media screen and (min-width: 1440px) {
    header {
        padding: 1rem 10rem;
    }
    
}
    
</style>