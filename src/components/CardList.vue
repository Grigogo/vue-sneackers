<script setup>
import ItemCard from './ItemCard.vue';

defineProps({
  items: Array,
})
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <ItemCard v-for="item in items" :key="item.id" :title="item.title" :image-url="item.imageUrl" :price="item.price" />
  </div>
</template>
