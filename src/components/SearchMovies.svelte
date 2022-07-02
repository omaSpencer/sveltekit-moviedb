<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	let searchQuery = '';

	function submitSearch() {
		goto(`/search/${searchQuery}`);
	}
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
	<input type="text" bind:value={searchQuery} name="search" placeholder="Search" required />
	{#if searchQuery.length >= 3}
		<button in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }} type="submit"
			>Search</button
		>
	{/if}
</form>

<style>
	.search {
		display: flex;
		align-items: center;
		margin-bottom: 2rem;
	}
	input {
		display: block;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 3px;
		margin-right: 0.25rem;
	}
	button {
		display: block;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 3px;
		background: #eee;
		cursor: pointer;
	}
</style>
