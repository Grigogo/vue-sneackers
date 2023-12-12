<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'

import HeaderView from './components/HeaderView.vue'
import CardList from './components/CardList.vue'
import DrawerCart from './components/DrawerCart.vue';

const items = ref([]);

onMounted(async () => {
  try {
    const { data } = await axios.get('https://79627c9d6c67b2e9.mokky.dev/items')

    items.value = data;
  } catch (err) {
    console.log(err);
  }
});


</script>

<template>
  <!-- <DrawerCart /> -->
  <div class="bg-white w-4/5 mx-auto rounded-xl shadow-xl mt-14">
    <HeaderView />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex gap-10">
          <select class="py-2 px-3 border rounded-md outline-none">
            <option value="">По названию</option>
            <option value="">По цене(дешёвые)</option>
            <option value="">По цене(дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/public/search.svg" alt="">
            <input class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400" placeholder="Поиск..."
              type="text">
          </div>
        </div>
      </div>



      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>

  </div>
</template>

<style scoped>
</style>
