<script>
	import { fade, slide, scale } from 'svelte/transition';
	import { flip } from 'svelte/animate';
	//import CardDetails
	import CardDetail from './CardDetail.svelte';
	export let cards = [];
</script>

<div class="poll-list">
	{#each cards as card (card.multiverseid)}
		<div in:fade|local animate:flip={{ duration: 500 }}>
			<CardDetail {card} on:handleShow />
		</div>
	{/each}
</div>

<style>
	.poll-list {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		grid-gap: 10px;
	}
</style>
