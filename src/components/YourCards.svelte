<script>
    import YourCardStore from "../stores/YourCardStore"
    import CardDetail from "./CardDetail.svelte"


</script>

<div class="card-list">
    {#each $YourCardStore as card (card.multiverseid)}
        <CardDetail {card} on:handleShow />
    {/each}
</div>

<style>
    .card-list {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>