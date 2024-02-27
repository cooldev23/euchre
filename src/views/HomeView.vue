<script setup>
import TheWelcome from '@/components/TheWelcome.vue';
import BaseView from './BaseView.vue';
</script>

<template>
  <BaseView> 
    <template #content>
      <TheWelcome/>
    </template>
  </BaseView>
</template>
