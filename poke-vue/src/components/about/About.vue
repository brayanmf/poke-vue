<script setup>
import { useRoute } from "vue-router";
import { ref } from "vue";
const route = useRoute();
const pokemon = ref(null);
(async () => {
  const res = await fetch(
    `https://pokeapi.co/api/v2/pokemon/${route.params.id}`
  );
  const data = await res.json();
  pokemon.value = data;
})();
</script>

<template>
  <div class="about">
    <div
      v-if="pokemon"
      class="w-3/12 m-auto bg-purple-100 mt-4 shadow-2xl flex justify-center flex-col items-center"
    >
      <h3 class="text-2xl text-green uppercase">{{ pokemon.name }}</h3>
      <div class="flex justify-center">
        <img
          class="w-48"
          :src="pokemon.sprites.front_shiny"
          alt="{{pokemon.name}}"
        />
        <img
          class="w-48"
          :src="pokemon.sprites.back_shiny"
          alt="{{pokemon.name}}"
        />
      </div>
      <h3 class="text-yellow-400">Types</h3>
      <div v-for="(item, id) in pokemon.types" :key="id">
        <span class="text-blue-400">{{ item.type.name }}</span>
      </div>
    </div>
  </div>
</template>
