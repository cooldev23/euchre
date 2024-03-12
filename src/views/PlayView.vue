<script setup>
import CardPlayer from '@/components/CardPlayer.vue';
import BaseView from './BaseView.vue';
import { ref, onBeforeMount } from 'vue'

// data
const players = ref([
  {
    name: 'Player 1', 
    cards: []
  },
  {
    name: 'Player 2', 
    cards: []
  },
  {
    name: 'Player 3', 
    cards: []
  },
  {
    name: 'Player 4', 
    cards: []
  }
])

const possibleCards = ref([
  '9H', '9S', '9D', '9C',
  'TH', 'TS', 'TD', 'TC',
  'JH', 'JS', 'JD', 'JC',
  'QH', 'QS', 'QD', 'QC',
  'KH', 'KS', 'KD', 'KC',
  'AH', 'AS', 'AD', 'AC'
]);

function dealCards() {
  for (let i = 0; i < possibleCards.value.length; i++) {
    let index = Math.floor(Math.random() * possibleCards.value.length),
    card = possibleCards.value.slice(index, index+1),
    player = players.value[Math.floor(Math.random() * players.value.length)];
    player.cards.push(card[0]);
  }
  
  
}

onBeforeMount(() => {
  dealCards()
})
</script>

<template>
  <BaseView>
    <template #content>
      <div class="h-1/3">
        <CardPlayer
          v-for="(player, index) in players"
          :key="index"
          :player="player"
        />
      </div>
    </template>
  </BaseView>
</template>