<template>
  <NavBar></NavBar>
  <slot name="body">
  </slot>
</template>

<script setup>
import NavBar from '@/components/NavBar.vue';
</script>