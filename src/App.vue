<script setup>
import MainScreen from './components/MainScreen.vue';
import InteractScreen from './components/InteractScreen.vue';

const statusMatch = 0;
function onHandleBeforeStart()  {
  
}
</script>

<template>
  <MainScreen v-if="statusMatch == 0" @onStart=""/>
  <InteractScreen v-if="statusMatch == 1"/>
</template>