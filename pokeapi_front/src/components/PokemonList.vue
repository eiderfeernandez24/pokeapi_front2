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
    background-color: blue;
    padding: 20px; 
    min-height: 100vh; 
}

.pokemon-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.pokemon-card {
    margin: 10px;
    padding: 10px;
    border: 1px solid #ccc; 
    border-radius: 5px; 
    width: calc(18% - 20px); 
    height: 280px;
    text-align: center;
    background-color: blue;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); 
    display: flex; /* Cambiado a flex para alinear elementos */
    flex-direction: column; /* Coloca los elementos en columna */
    align-items: center; /* Centra los elementos horizontalmente */
    justify-content: space-between; /* Espacia los elementos verticalmente */
}

.pokemon-card img {
    width: 160px; 
    height: 160px; 
    background-color: white; 
    border-radius: 5px; 
    padding: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    margin-top: 35px;
}

.pokemon-name {
    color: white;
    font-size: 18px; 
    margin-top: 10px; 
}
</style>
