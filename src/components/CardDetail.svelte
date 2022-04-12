<script>
	import Card from './shared/Card.svelte';
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	const handleShow = (card) => {
		console.log('show');
		dispatch('handleShow', card);
	};

	export let card;
</script>

<Card
	list={true}
	show={false}
	on:click={() => {
		handleShow(card);
	}}
>
	<img src={card.imageUrl} alt="{card.name} image" />
</Card>

<style>
	img {
		width: 310px;
	}
</style>
