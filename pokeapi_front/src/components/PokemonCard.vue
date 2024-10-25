<template>
  <div class="pokemon-card">
    <img :src="pokemonImage" alt="Pokémon" />
    <h2 class="pokemon-name">{{ formattedName }}</h2> <!-- El nombre del Pokémon -->
  </div>
</template>

<script>
export default {
  props: {
    pokemon: {
      type: Object,
      required: true,
    },
  },
  computed: {
    formattedName() {
      return this.pokemon.name.charAt(0).toUpperCase() + this.pokemon.name.slice(1);
    },
    pokemonImage() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${this.pokemon.id}.png`;
    },
  },
};
</script>
