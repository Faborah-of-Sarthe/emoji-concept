<template>
    <header>
        <div class="wrapper">
            <h1>Emoji Concept</h1>
            <SelectedEmojis />
        </div>
    </header>
</template>

<script setup>
    import SelectedEmojis from './SelectedEmojis.vue';
</script>

<style>

h1 {
    text-align: center;
}

header {
    background-color: #f5f5f5;
    padding: 1rem;
    width: 100%;
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