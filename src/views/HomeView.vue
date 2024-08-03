<template>
  <div>
    <div class="m-auto">
      <Header />
      <div>
        <programDay />
        <place />
        <detail />
        <formVue/>
      </div>
    </div>


  </div>
</template>

<script setup>
import Header from '@/components/Header/Header.vue'
import programDay from '@/components/programDay/programDay.vue'
import place from '@/components/Place/place.vue'
import detail from '@/components/Detals/Detals.vue'
import formVue from '@/components/Form/form.vue'
</script>