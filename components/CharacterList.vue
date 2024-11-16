<template>
    <div class="character-list">
        <CharacterCard v-for="character in characters" :key="character.id" :character="character" />

    </div>
</template>

<script>
import CharacterCard from './CharacterCard.vue';

export default {
    props: {
        characters: {
            type: Array,
            required: true,
        },
    },
    components: {
        CharacterCard,
    },
};
</script>

<style scoped>
.character-list {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    justify-content: center;
    margin-top: 2rem;
}
</style>