<script setup>
    import CardFlip from './Card.vue';

    import { defineProps } from 'vue';

    const props = defineProps({
        cardsContext: {
            type: Array,
            required: true,
            default: function() {
                return [];
            },
        }
    });
</script>

<template>
    <h1>Interact</h1>
    <CardFlip v-for="(card, index) in cardsContext" :key="index" :imgBackFaceUrl="`images/${card}.png`"></CardFlip>
</template>