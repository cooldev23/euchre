<script setup>
import CardPlayer from "@/components/CardPlayer.vue";
import BaseView from "./BaseView.vue";
import { ref, onBeforeMount } from "vue";

// data
const players = ref([
  {
    name: "Player 1",
    cards: [],
    totalCards: 0,
    isDealer: false
  },
  {
    name: "Player 2",
    cards: [],
    totalCards: 0,
    isDealer: false
  },
  {
    name: "Player 3",
    cards: [],
    totalCards: 0,
    isDealer: false
  },
  {
    name: "Player 4",
    cards: [],
    totalCards: 0,
    isDealer: false
  },
]);

const possibleCards = ref([
  "9H",
  "9S",
  "9D",
  "9C",
  "TH",
  "TS",
  "TD",
  "TC",
  "JH",
  "JS",
  "JD",
  "JC",
  "QH",
  "QS",
  "QD",
  "QC",
  "KH",
  "KS",
  "KD",
  "KC",
  "AH",
  "AS",
  "AD",
  "AC",
]);

function dealCards() {
  for (let i = 0; i < 20; i++) {
    let index = Math.floor(Math.random() * possibleCards.value.length),
      card = possibleCards.value.splice(index, 1);
         
    if (!doAllPlayersHaveFiveCards()) {
      let player = getPlayer();
      player.cards.push(card[0]);
    }
  }
}

function getPlayer() {
  let playersWithoutFiveCards = players.value.filter((item) => item.cards.length < 5);
  let player = playersWithoutFiveCards[Math.floor(Math.random() * playersWithoutFiveCards.length)];

  return player;
}

function doAllPlayersHaveFiveCards() {
  let playersWithoutFiveCards = players.value.filter((item) => item.cards.length < 5);

  if (playersWithoutFiveCards.length) {
    return false;
  }

  return true;
}

onBeforeMount(() => {
  dealCards();
});
</script>

<template>
  <BaseView>
    <template #content>
      <div class="h-1/3">
        <CardPlayer v-for="(player, index) in players" :key="index" :player="player" />
      </div>
    </template>
  </BaseView>
</template>
