<script>
	import YourCardStore from '../stores/YourCardStore';
	import Card from './shared/Card.svelte';
	import Button from './shared/Button.svelte';
	import Formats from '../components/shared/Formats.svelte';
	import { createEventDispatcher } from 'svelte';
	import { text } from 'svelte/internal';
	export let selectedCard;

	let dispatch = createEventDispatcher();

	const handleAdd = () => {
		YourCardStore.update((currentCards) => {
			return [selectedCard, ...currentCards];
		});
		dispatch('add');
	};
</script>

<div class="back-button">
	<p class="back-button" on:click>back</p>
</div>
<div class="card-details">
	<img src={selectedCard.imageUrl} alt="{selectedCard.name} image" />

	<Card
		show={true}
		list={false}
		optionalClass="card-detail-card"
		colorClass={selectedCard.colors ? selectedCard.colors[0].toLowerCase() : 'colorless'}
	>
		<h1>{selectedCard.name}</h1>
		<div class="detail-container">
			<div class="details">
				<h3 id="type">{selectedCard.originalType}</h3>
				<h3 id="mana-value">Mana cost: {selectedCard.manaCost}</h3>
			</div>
			<div class="details">
				<h3 id="rarity">Rarity: {selectedCard.rarity}</h3>
				<h3 id="set-name">Set Name: {selectedCard.setName}</h3>
			</div>
			<div class="text-details">
				{#each selectedCard.text.split('\n') as lines (Math.random())}
					<h3>{lines}</h3>
				{/each}
			</div>
		</div>
		<Formats legalities={selectedCard.legalities} />
	</Card>
	<Button on:click={handleAdd}>Add to Your Cards</Button>
</div>

<style>
	img {
		width: 30%;
		border-radius: 12px;
		box-shadow: 1px 1px 8px rgb(0 0 0 / 50%);
	}
	.card-details {
		margin: 0 auto;
		text-align: center;
	}
	.back-button {
		cursor: pointer;
	}
	.detail-container {
		display: flex;
		flex-direction: column;
	}
	.details {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.text-details {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 0;
	}
	h1 {
		color: #3e2d2d;
		padding: 5% 0;
		font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
	}
	h3 {
		color: #3e2d2d;
		padding: 0 2%;
		font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
	}
</style>
