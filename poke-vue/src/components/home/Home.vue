<script setup>
import { ref } from "vue";

const pokemon = ref([]);
const nameIdLookup = ref({});
const text = ref("");
const filteredPokemon = ref(() => {
  return pokemon.value.filter((item) => item.name.includes(text.value));
}); //lo ideal es recibirlo como aprametro pero bueno ;]
//si tenemoe el texto dentro del nombre del pokemon formamos un nuevo array con los pokemon que contengan el texto
(async () => {
  const res = await fetch("https://pokeapi.co/api/v2/pokemon?offset=0");
  const data = await res.json();
  pokemon.value = data.results;

  nameIdLookup.value = data.results.reduce(
    (obj, data, id) => (obj = { ...obj, [data.name]: id + 1 }),
    {}
  );
})();
</script>

<template>
  <div class="greetings">
    <h3>poke-api</h3>
  </div>
  <div class="w-full flex items-center flex-col m-auto">
    <div class="w-1/3">
      <input
        class="mt-10 p-4 border-2 border-green-500 rounded"
        type="text"
        placeholder="Search"
        v-model="text"
      /><!--v-model-instanciando con nuestro ref-->
    </div>

    <div class="mt-10 w-1/3 flex flex-wrap">
      <div
        class="ml-4 text-2x text-blue-500-200"
        v-for="(item, id) in filteredPokemon()"
        :key="id"
      >
        <router-link :to="`/about/${nameIdLookup[item.name]}`">
          {{ item.name }}
        </router-link>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
