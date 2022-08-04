<script>
import PokemanCard from '../component/pokemanCard.svelte';
import {pokemon} from '../store/pokerStores'
import About from './about.svelte';

let searchTerm = '';
let filteredPokemon =[];

$:{
    console.log(searchTerm)
    if(searchTerm){
        filteredPokemon = $pokemon.filter(pokeman => pokeman.name.toLowerCase().includes(searchTerm.toLocaleLowerCase()))
    }else{
        filteredPokemon =[...$pokemon]
    }
}
</script>

<svelte:head>
    <title>Nacho pokerdex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase ">Welcome to SvelteKit pokerdex</h1>

<input type="text" placeholder="Search..." bind:value={searchTerm} class="w-full rounded-md text-lg p-4 border-2 border-gray-200" >

<div class="py-4 grid gap-4 md:grid-cols-2 gird-cols-1">

    {#each filteredPokemon as pokeman}
    <p><PokemanCard {pokeman} /></p>
    {/each}
</div>

<style>

</style>
