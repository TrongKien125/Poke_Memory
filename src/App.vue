<script setup>
import MainScreen from './components/MainScreen.vue';
import InteractScreen from './components/InteractScreen.vue';
import CoppyRightScreen from './components/CoppyRightScreen.vue';
import ResulScreen from './components/ResulScreen.vue';

import { shuffled } from './utils/array';
import { ref } from 'vue';

const statusMatch = ref(0);
const setting = ref({
  totalOfBlocks : 0,
  cardsContext : [],
  startedAt : null,
});

function onHandleBeforeStart(config)  {
  setting.value.totalOfBlocks = config.totalOfBlocks;
  const fisrtCards = Array.from(
    {length: setting.value.totalOfBlocks / 2 },
    (_, i) => i + 1
  );
  const secondCards = [...fisrtCards];
  const cards = [...fisrtCards, ...secondCards];
  setting.value.cardsContext = shuffled(shuffled(cards));
  setting.value.startedAt = new Date().getTime();
  statusMatch.value = 1;
}

</script>

<template>
  <MainScreen v-if="statusMatch == 0" @onStart="onHandleBeforeStart"/>
  <InteractScreen v-if="statusMatch == 1" :cardsContext="setting.cardsContext"/>
</template>