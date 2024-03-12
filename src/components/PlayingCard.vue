<template>
  <img :src="imageUrl" alt="" class="w-16 h-24">
</template>

<script setup>
import { ref } from 'vue'

// props
const props = defineProps({
    cardValue: String,
});

//data
const imageUrl = ref(getImageUrl(props.cardValue + '.svg'))

// named functions
function getImageUrl(name) {
    return new URL(`/src/assets/images/card-svgs/${name}`, import.meta.url).href
}
</script>