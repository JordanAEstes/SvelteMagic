<script>
	import CardList from '../components/CardList.svelte';
	import Search from '../components/Search.svelte';
	import Tabs from '../components/shared/Tabs.svelte';
	import Header from '../components/shared/Header.svelte';
	import CardShow from '../components/CardShow.svelte';
	import YourCards from '../components/YourCards.svelte';
	let items = ['Search', 'Your Cards'];
	let activeItem = 'Search';
	let activeView = 'List';
	let cards = [];
	let selectedCard;

	const tabChange = (e) => {
		activeItem = e.detail;
	};

	const handleSearch = async (e) => {
		cards = [];
		activeView = 'List';
		let searchQuery = e.detail;
		let response = await fetch(`https://api.magicthegathering.io/v1/cards?name=${searchQuery}`);
		let body = await response.json();
		let results = body.cards;
		cards = [...new Map(results.map((card) => [card['multiverseid'], card])).values()];
		cards.sort((a, b) => (a.name > b.name ? 1 : -1));
		cards = cards.filter((card) => {
			console.log(card.name, card.imageUrl != undefined);
			return card.imageUrl != undefined;
		});
		console.log(cards);
	};

	const handleShow = (e) => {
		activeItem = 'Search';
		activeView = 'Show';
		selectedCard = e.detail;
		console.log(activeItem, activeView, selectedCard);
	};

	const handleBack = () => {
		activeView = 'List';
	};
	const handleAdd = () => {
		activeView = 'List';
		activeItem = 'Your Cards';
	};
</script>

<Header />
<main>
	<Tabs {items} {activeItem} on:tabChange={tabChange} />
	{#if activeItem === 'Search'}
		<Search on:search={handleSearch} />
		{#if activeView == 'List'}
			{#if cards.length != 0}
				<CardList {cards} on:handleShow={handleShow} />
			{/if}
		{:else if activeView == 'Show'}
			<CardShow {selectedCard} on:click={handleBack} on:add={handleAdd} />
		{/if}
	{:else if activeItem === 'Your Cards'}
		<YourCards on:handleShow={handleShow} />
	{/if}
</main>

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
