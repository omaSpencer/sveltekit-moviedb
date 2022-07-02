<script context="module">
	const API_KEY = '630df4ae7871ef8ce0b5d07bb9612e43';
	export async function load({ fetch, params }) {
		const response = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${API_KEY}&query=${params.id}&page=1`
		);
		const data = await response.json();
		if (response.ok) {
			return {
				props: {
					movies: data.results,
					title: `Search results for "${params.id}"`
				}
			};
		}
	}
</script>

<script>
	export let movies;
	export let title;
	import Movies from '../../components/Movies.svelte';
</script>

<main>
	<Movies {movies} {title} />
</main>

<style>
	main {
		max-width: 1280px;
		margin: 0 auto;
		padding: 0 20px;
	}
</style>
