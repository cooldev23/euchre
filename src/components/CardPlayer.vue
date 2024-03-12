<template>
  <h5>{{ player.name }}</h5>
  <div class="cards">
    <PlayingCard
      v-for="(card, index) in player.cards"
      :key="index"
      :card-value="card"
    />
  </div>
</template>

<script setup>
  import PlayingCard from './PlayingCard.vue';

  // props
  const props = defineProps({
    player: {
      type: Object,
      default: () => {
        return {}
      }
    }
  })
</script>