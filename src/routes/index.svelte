<script context="module">
	export async function load({ page }) {
		const url = `https://pokeapi.co/api/v2/pokemon?limit=150`;
		const urlResponse = await fetch(url); // get the response returns a promise, so we await
		const responseData = await urlResponse.json(); // get data from the response, return it as json
		const mappedData = responseData.results.map((data, index) => {
			return {
				name: data.name,
				id: index + 1,
				image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${
					index + 1
				}.png`
			};
		});
		return { props: { pokemon: mappedData } };
	}
</script>

<script>
	// import stores and components here:
	import Card from '../lib/card.svelte'
	export let pokemon;

	let searchTerm = ``;
	let searchResults = [];

	// this syntax provides a reactive scope
	// updates everytime searchTerm is changed
	$: {
		console.log(searchTerm);
		// if there is a search term
		if (searchTerm) {
			// for each item in pokemonStore store, check if it's name contains the searchterm
			// convert search term and item name to lowercase before checking (user can use upper or lower)
			searchResults = pokemon.filter((item) =>
				item.name.toLowerCase().includes(searchTerm.toLocaleLowerCase())
			);
		} else {
			// filtered search is a copy of the original store
			searchResults = [...pokemon];
		}
	}
</script>

<svelte:head>
	<title>Welcome to the SvelteKit Pokedex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">SvelteKit Pokedex</h1>

<input
	class="w-full rounded-md text-lg p-4 text-gray-500 border-2 border-gray-200 bg-gray-800"
	bind:value={searchTerm}
	type="text"
	placeholder="Search Pokemon..."
/>


<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each searchResults as item}
		<p>
			<Card cardItem={item} />
		</p>
	{/each}
</div>
