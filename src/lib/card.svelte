<script>
    import { fade } from 'svelte/transition';
    export let cardItem
</script>

<a class="no-underline p-6 bg-gray-800 text-gray-500 text-center rounded-md shadow-lg border-2 border-gray-200 flex flex-col items-center"
href={`/pokemon/${cardItem.id}`} transition:fade>
<!-- padding 6, background gray, text gray, center text, rounded border, box shadow, flex, column flex, center items -->
    <img class="h-40 w-40" src={cardItem.image} alt={cardItem.name}>
<h2 class="uppercase text-2xl">{cardItem.id}. {cardItem.name}</h2>
</a>