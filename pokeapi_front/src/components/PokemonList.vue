<template>
<div class="pokemon-list">
    
    <div class="pokemon-container">
    <PokemonCard
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        :pokemon="pokemon"
    />
    </div>
</div>
</template>

<script>
import axios from 'axios';
import PokemonCard from './PokemonCard.vue';

export default {
components: {
    PokemonCard,
},
data() {
    return {
    pokemons: [],
    };
},
created() {
    this.fetchPokemons();
},
methods: {
    async fetchPokemons() {
    try {
        const response = await axios.get('https://pokeapi.co/api/v2/pokemon/?offset=0&limit=151');
        this.pokemons = response.data.results.map((pokemon, index) => ({
        id: index + 1, // Asignamos un ID desde 1 hasta 151
        name: pokemon.name,
        url: pokemon.url,
        }));
    } catch (error) {
        console.error('Error fetching Pokémon:', error);
    }
    },
},
};
</script>

<style>
.pokemon-list {
text-align: center;
}

.pokemon-container {
display: flex;
flex-wrap: wrap;
justify-content: center;
}
</style>
