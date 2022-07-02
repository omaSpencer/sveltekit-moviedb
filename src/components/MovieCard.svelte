<script>
	export let movie;
</script>

<article>
	<a sveltekit:prefetch sveltekit:noscroll href={`/movie/${movie.id}`}>
		<img
			src={!!movie.poster_path
				? `https://image.tmdb.org/t/p/w500/${movie.poster_path}`
				: 'https://loremflickr.com/500/740'}
			alt={movie.title}
		/>
	</a>
	<h3>{movie.title}</h3>
	<p>{movie.overview.substring(0, 120) + '...'}</p>
</article>

<style>
	article {
		grid-column: span 1;
	}
	a,
	a:visited,
	a:hover,
	a:active {
		text-decoration: none;
		color: inherit;
	}
	h3 {
		margin-bottom: 20px;
	}
	img {
		width: 100%;
		height: auto;
		margin-bottom: 10px;
		border-radius: 1rem;
		transition: all ease-in-out 0.25s;
	}
	img:hover {
		transform: scale(1.05) translateY(-2%);
		box-shadow: 0 0 12px 4px rgba(0, 0, 0, 0.33);
	}
</style>
