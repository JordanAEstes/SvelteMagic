<script>
	import Button from './Button.svelte';
	import { onMount } from 'svelte';

	let formats = [
		{ format: 'Alchemy', legality: 'Not Legal', id: 0 },
		{ format: 'Brawl', legality: 'Not Legal', id: 1 },
		{ format: 'Commander', legality: 'Not Legal', id: 2 },
		{ format: 'Duel', legality: 'Not Legal', id: 3 },
		{ format: 'Future', legality: 'Not Legal', id: 4 },
		{ format: 'Gladiator', legality: 'Not Legal', id: 5 },
		{ format: 'Historic', legality: 'Not Legal', id: 6 },
		{ format: 'Historicbrawl', legality: 'Not Legal', id: 7 },
		{ format: 'Legacy', legality: 'Not Legal', id: 8 },
		{ format: 'Modern', legality: 'Not Legal', id: 9 },
		{ format: 'Oldschool', legality: 'Not Legal', id: 10 },
		{ format: 'Pauper', legality: 'Not Legal', id: 11 },
		{ format: 'Paupercommander', legality: 'Not Legal', id: 12 },
		{ format: 'Penny', legality: 'Not Legal', id: 13 },
		{ format: 'Pioneer', legality: 'Not Legal', id: 14 },
		{ format: 'Premodern', legality: 'Not Legal', id: 15 },
		{ format: 'Standard', legality: 'Not Legal', id: 16 },
		{ format: 'Vintage', legality: 'Not Legal', id: 17 }
	];
	let formatsFirstColumn = [];
	let formatsSecondColumn = [];
	export let legalities = {};
	var legalityObject = legalities.reduce(
		(legalObj, legality) => ((legalObj[legality.format] = legality.legality), legalObj),
		{}
	);
	onMount(() => {
		formats.map((format) => {
			if (format.format in legalityObject) {
				format.legality = legalityObject[format.format];
			}
		});
		console.log(formats);
		formatsFirstColumn = formats.slice(0, 9);
		console.log(formatsFirstColumn);

		formatsSecondColumn = formats.slice(9, 18);
		console.log(formatsSecondColumn);
	});
</script>

<div class="row-container">
	<div class="column-container">
		{#each formatsFirstColumn as format (format.id)}
			<div class="format-container">
				<div class="chip {format.legality.toLowerCase().split(' ').join('-')}">
					{format.legality}
				</div>
				<div>{format.format}</div>
			</div>
		{/each}
	</div>
	<div class="column-container">
		{#each formatsSecondColumn as format (format.id)}
			<div class="format-container">
				<div class="chip {format.legality.toLowerCase().split(' ').join('-')}">
					{format.legality}
				</div>
				<div>{format.format}</div>
			</div>
		{/each}
	</div>
</div>

<style>
	.column-container {
		display: flex;
		flex-direction: column;
	}
	.row-container {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		border: 3px solid;
		padding: 5px;
		border-radius: 4px;
	}
	.format-container {
		display: flex;
		flex-direction: row;
	}
	.chip {
		width: 100px;
		border-radius: 8px;
		border: 2px solid;
	}
	.banned {
		background-color: #bb7777;
	}
	.legal {
		background-color: #78907b;
	}
	.restricted {
		background-color: #dfd8ba;
	}
	.not-legal {
		background-color: #bbbbbb;
	}
</style>
