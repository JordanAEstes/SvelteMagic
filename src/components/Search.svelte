<script>
	import { createEventDispatcher } from 'svelte';
	import Button from './shared/Button.svelte';

	let dispatch = createEventDispatcher();
	let searchQuery;

	const submitHandler = async () => {
		console.log(searchQuery);
		dispatch('search', searchQuery);
	};
</script>

<form on:submit|preventDefault={submitHandler}>
	<div class="form-field">
		<input type="text" id="search" bind:value={searchQuery} />
		<Button>Search</Button>
	</div>
</form>

<style>
	form {
		width: 400px;
		margin: 0 auto;
		text-align: center;
	}
	.form-field {
		display: flex;
		flex-direction: row;
		margin: 18px auto;
	}
	input {
		flex: 1;
		height: 25px;
		width: 100%;
		border-radius: 6px;
	}
</style>
