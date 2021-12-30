<!-- server side redering, fetch data before it is displayed to the user -->
<script context="module">
	export async function load({ page }) {
		// binds this id to the dynamic [id] arg in [id].svelte
		const id = page.params.id;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
		const urlResponse = await fetch(url);
		const pokemon = await urlResponse.json();
		return { props: { pokemon } };
	}
</script>

<script>
	export let pokemon;
	const types = pokemon.types;
</script>

<div class="border-28 border-bg-yellow-600 mt-8 rounded-lg shadow-lg bg-purple-900">
	<!-- VSTACK -->
	<div class="flex flex-col items-center ">
		<!-- HSTACK -->
		<div class="flex flex-row">
			<h1 class="mx-15 text-4xl text-center">
				{pokemon.name[0].toUpperCase() + pokemon.name.substring(1)}
			</h1>
			<h1 class="mt-6.5 mx-15 text-red-500">{pokemon.stats[0]['base_stat']} HP</h1>
		</div>
		<img
			class="border-8 border-bg-yellow-600 rounded-lg shadow-lg bg-gray-300 "
			src={pokemon.sprites.other['official-artwork']['front_default']}
			alt={pokemon.name}
		/>

		<!-- HSTACK -->
		<div class="flex flex-row items-center shadow-lg bg-yellow-600 my-6 mx-8 px-8">
			<h4 class="px-2">Type:</h4>
			<h4 class="px-2">
				{#each pokemon.types as item}{item.type.name.toUpperCase() + ' '}{/each}
			</h4>
			<h4 class="px-2">Height: {pokemon.height}</h4>
			<h4 class="px-2">Weight: {pokemon.weight}</h4>
			<h4>Abilities:</h4>
			<h4 class="px-2 items-center">
				{#each pokemon.abilities as ability}{ability.ability.name.toUpperCase() + ' '}{/each}
			</h4>
		</div>
		<!-- HSTACK -->
		<div class="flex flex-col bg-yellow-600 mb-6 mt-2 mx-8 p-4 rounded-lg shadow-lg">
			<div
				class="flex flex-row items-center  pl-15 border-2 p-2 mx-2 mt-2 mb-8 bg-gray-300 rounded-lg shadow-lg"
			>
				<h3 class="px-2">Attack: {pokemon.stats[1]['base_stat']}</h3>
				<h3 class="px-2">Defense: {pokemon.stats[2]['base_stat']}</h3>
				<h3 class="px-2">Special Attack: {pokemon.stats[3]['base_stat']}</h3>
				<h3 class="px-2">Special Defense: {pokemon.stats[4]['base_stat']}</h3>
				<h3 class="px-2">Speed: {pokemon.stats[4]['base_stat']}</h3>
			</div>

			<div
				class="flex flex-row items-center pl-4 border-2 p-2 mx-2 mb-4 bg-gray-300 rounded-lg shadow-lg">
			
			<div class="py-4 px-2 grid gap-4 md:grid-cols-4 grid-cols-2">
				{#each pokemon.moves as item}
					<p>
						{item.move.name.toUpperCase() + ' '}
					</p>
				{/each}
			</div>
			<!-- VSTACK -->
		</div>
	</div>
</div>
</div>