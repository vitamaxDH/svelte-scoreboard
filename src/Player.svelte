<script>
    import {createEventDispatcher} from 'svelte';

    export let name;
    export let points;

    const dispatch = createEventDispatcher();
    let showControls = false;

	const addPoint = () => (points += 1);
	const removePoint = () => (points -= 1);
    const toggleControls = () => (showControls = !showControls);
    const onDelete = () => dispatch('removeplayer', name);
</script>


<style>
	h1 {
		color: #204f6e;
	}
	
	h3 {
		margin-bottom: 10px;
	}

</style>

<div class="card">
    <h1>
        {name}
        <button class="btn btn-sm" on:click="{toggleControls}">
            {#if showControls}-{:else}+{/if}
        </button>
        <button class="btn btn-danger btn-sm" on:click={onDelete} >Delete Player</button>
    </h1>
    <h3>points : {points}</h3>
    {#if showControls}
        <button class="btn" on:click="{addPoint}">+1</button>
        <button class="btn btn-dark" on:click="{removePoint}">-1</button>
        <input type="number" bind:value="{points}" />
    {/if}
</div>

