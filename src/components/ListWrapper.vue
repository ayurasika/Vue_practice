<template>
    <ListItem
      v-for="(item, i) in items"
      :key="i"
      :data="item"
    >
      <template #default="{ data }">
        <slot :data="data" />
      </template>
    </ListItem>
  </template>
  
  <script setup>
  import ListItem from './ListItem.vue';
  
  defineProps({
    items: Array
  });
  </script>