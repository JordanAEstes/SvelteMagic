<script>
	export let list = true;
	export let show = false;
	export let optionalClass;
</script>

<div class="card {optionalClass}" class:list class:show on:click>
	<slot />
</div>

<style>
	.card {
		background: #fff;
		border-radius: 15px;
		text-align: center;
	}
	.show {
		width: 50%;
		box-shadow: 1px 1px 8px rgb(0 0 0 / 50%);
	}
	.card-detail-card {
		width: 60%;
		margin-left: 20%;
		box-shadow: 1px 1px 8px rgb(0 0 0 / 50%);
	}
</style>
