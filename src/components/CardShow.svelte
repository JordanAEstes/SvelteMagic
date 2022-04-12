<script>
	import Card from './shared/Card.svelte';
	export let selectedCard;
</script>

<div class="back-button">
	<p class="back-button" on:click>back</p>
</div>
<div class="card-details">
	<img src={selectedCard.imageUrl} alt="{selectedCard.name} image" />

	<Card show={true} list={false} optionalClass="card-detail-card">
		<h1>{selectedCard.name}</h1>
		<div class="details">
			<h3>{selectedCard.originalType}</h3>
			<h3>{selectedCard.cmc}</h3>
		</div>
	</Card>
</div>

<style>
	img {
		width: 30%;
		box-shadow: 1px 1px 8px rgb(0 0 0 / 50%);
	}
	.card-details {
		margin: 0 auto;
		text-align: center;
	}
	.back-button {
		cursor: pointer;
	}
	.details {
		display: flex;
		flex-direction: row;
	}
	h1 {
		color: #3e2d2d;
		padding: 5% 0;
		font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
	}
	h3 {
		color: #3e2d2d;
		padding: 5% 0;
		font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
	}
</style>
