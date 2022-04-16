<script>
	export let list = true;
	export let show = false;
	export let optionalClass;
	export let colorClass;
</script>

<div class="card {optionalClass} {colorClass}" class:list class:show on:click>
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
		width: 70%;
		margin-left: 15%;
		box-shadow: 1px 1px 8px rgb(0 0 0 / 50%);
		background-color: #eee;
	}
	.white {
		background-color: #f3f1e7;
		border: 4px solid #dfd8ba;
	}
	.blue {
		background-color: #b7c2cf;
		border: 4px solid #6a8cb6;
	}
	.black {
		background-color: #bbbbbb;
		border: 4px solid #343434;
	}
	.red {
		background-color: #e6d1d1;
		border: 4px solid #bb7777;
	}
	.green {
		background-color: #d0d9d3;
		border: 4px solid #78907b;
	}
</style>
