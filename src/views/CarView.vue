<script setup>
import { useRoute } from 'vue-router';
import { ref, onBeforeMount } from "vue";
import cars from "../data.json";

const car = ref(null);
const route = useRoute();

onBeforeMount(() => {
  car.value = cars.find(c => c.id === parseInt(route.params.id));
});
</script>
<template>
  <div class="container">
    <div v-if="car">
      <h1>The Car</h1>
      <p>Make: {{ car.make }}</p>
      <p>Body: {{ car.body }}</p>
      <p>Price: {{ car.price }}</p>
      <p>Year: {{ car.year }}</p>
    </div>
    <div v-else>
      Car Not Found!
    </div>
  </div>
</template>