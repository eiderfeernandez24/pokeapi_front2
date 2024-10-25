<template>
  <div class="pokemon-card">
    <img :src="pokemonImage" alt="Pokémon" />
    <h2>{{ formattedName }}</h2>
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

<style>
.pokemon-card {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc; /* Color del borde */
  border-radius: 5px; /* Esquinas redondeadas */
  width: 150px;
  text-align: center;
  background-color: white; /* Color de fondo blanco para las cartas */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Sombra ligera para un mejor efecto visual */
}

.pokemon-card img {
  width: 100px;
  height: 100px;
}
</style>
