<template>
  <NavBar></NavBar>
  <main>
    <slot name="content">
    </slot>
  </main>
</template>

<script setup>
import NavBar from '@/components/NavBar.vue';
</script>