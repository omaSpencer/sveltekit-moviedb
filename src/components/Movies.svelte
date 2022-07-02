<script>
	export let movies;
	export let title;
	import MovieCard from './MovieCard.svelte';
</script>

<h1>{title}</h1>
<div class="movies">
	{#each movies as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h1 {
		margin-bottom: 30px;
	}
	.movies {
		display: grid;
		column-gap: 1.5rem;
		row-gap: 3rem;
		grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
	}
</style>
