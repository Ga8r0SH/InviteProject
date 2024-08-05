<template>
    <div class="container mx-auto p-4">
      <h1 class="text-3xl font-bold mb-6">Список гостей на свадьбу</h1>
      <div v-if="loading" class="text-center">Загрузка...</div>
      <div v-else-if="error" class="text-center text-red-500">{{ error }}</div>
      <div v-else>
        <div v-for="guest in guests" :key="guest.id" class="p-4 mb-4 bg-white rounded shadow">
          <div class="flex items-center justify-between">
            <div>
              <h2 class="text-xl font-semibold">{{ guest.first_name }} {{ guest.last_name }}</h2>
              <p v-if="guest.attending_with_partner" class="text-gray-600">
                Придет с партнером: {{ guest.partner_first_name }} {{ guest.partner_last_name }}
              </p>
              <p v-else-if="guest.attending && !guest.attending_with_partner" class="text-gray-600">Приду один</p>
              <p v-else class="text-gray-600">Не придет</p>
            </div>
            <div class="text-right">
              <p class="text-gray-600">Предпочтение в напитках: {{ formatDrinkPreferences(guest.drink_preferences) }}</p>
              <p class="text-gray-400 text-sm">Дата добавления: {{ formattedDate(guest.created_at) }}</p>
              <button @click="deleteGuest(guest.id)" class="text-red-500 hover:text-red-700 mt-2">Удалить</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import axios from 'axios';
  
  const guests = ref([]);
  const loading = ref(true);
  const error = ref(null);
  
  const drinkPreferences = {
    whiteWine: 'Белое вино',
    redWine: 'Красное вино',
    champagne: 'Шампанское',
    cognac: 'Коньяк',
    nonAlcoholic: 'Без алкашки'
  };
  
  const formattedDate = (date) => {
    return new Date(date).toLocaleDateString('ru-RU');
  };
  
  const formatDrinkPreferences = (preferences) => {
    if (!preferences) return 'Нет предпочтений';
    return preferences.split(',').map(pref => drinkPreferences[pref.trim()]).join(', ');
  };
  
  const fetchGuests = async () => {
    try {
      const response = await axios.get('https://alexandrsofia.dif.md/api/responses');
      guests.value = response.data;
    } catch (err) {
      error.value = 'Не удалось загрузить данные.';
    } finally {
      loading.value = false;
    }
  };
  
  const deleteGuest = async (id) => {
    try {
      await axios.delete(`https://alexandrsofia.dif.md/api/responses/${id}`);
      guests.value = guests.value.filter(guest => guest.id !== id);
    } catch (err) {
      error.value = 'Не удалось удалить гостя.';
    }
  };
  
  onMounted(() => {
    fetchGuests();
  });
  </script>
  
  <style scoped>
  /* Ваши стили здесь */
  </style>
  