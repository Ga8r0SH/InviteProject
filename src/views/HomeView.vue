<template>
  <div>
    <div class="m-auto">
      <Header />
      <div>

        <programDay />
        <place />
      </div>
    </div>


  </div>
</template>

<script setup>
import Header from '@/components/Header/Header.vue'
import programDay from '@/components/programDay/programDay.vue'
import place from '@/components/Place/place.vue'
</script>