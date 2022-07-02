<script context="module">
	const API_KEY = '630df4ae7871ef8ce0b5d07bb9612e43';
	export async function load({ fetch }) {
		const response = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`);
		const data = await response.json();
		if (response.ok) {
			return {
				props: {
					popular: data.results
				}
			};
		}
	}
</script>

<script>
	import Movies from '../components/Movies.svelte';
	import SearchMovies from '../components/SearchMovies.svelte';
	export let popular;
	import { fly } from 'svelte/transition';
</script>

<main in:fly={{ y: 50, duration: 500 }} out:fly={{ y: 50, duration: 500 }}>
	<SearchMovies />
	<Movies movies={popular} title="Popular Movies" />
</main>

<style>
	main {
		max-width: 1280px;
		margin: 0 auto;
		padding: 0 20px;
	}
</style>
