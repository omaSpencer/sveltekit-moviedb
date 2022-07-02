<script context="module">
	const API_KEY = '630df4ae7871ef8ce0b5d07bb9612e43';
	export async function load({ fetch, params }) {
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${API_KEY}`
		);
		const movieDetail = await response.json();
		if (response.ok) {
			return {
				props: {
					movieDetail
				}
			};
		}
	}
</script>

<script>
	export let movieDetail;
	import { fly } from 'svelte/transition';
</script>

<svelte:head>
	<title>{movieDetail.original_title}</title>
</svelte:head>

<article in:fly={{ y: 50, duration: 500 }} out:fly={{ y: 50, duration: 500 }}>
	<figure>
		<img
			src={`https://image.tmdb.org/t/p/original/${movieDetail.poster_path}`}
			alt={movieDetail.original_title}
		/>
	</figure>
	<div class="details">
		<h1>{movieDetail.original_title}</h1>
		<p class="date">
			Release date: <span>{new Date(movieDetail.release_date).toDateString()}</span>
		</p>
		<ul class="genres">
			{#each movieDetail.genres as genre}
				<li>{genre.name}</li>
			{/each}
		</ul>
		<p>{movieDetail.overview}</p>
	</div>
</article>

<style>
	article {
		min-height: 100vh;
		background-repeat: no-repeat;
		background-size: contain;
	}
	figure img {
		width: 100%;
		height: auto;
		max-height: 80vh;
		object-fit: cover;
	}
	.details {
		max-width: 768px;
		margin: 0 auto;
		padding: 40px 20px;
	}
	h1 {
		font-size: 3.6rem;
		margin-bottom: 1.2rem;
	}
	p {
		font-size: 1.6rem;
		line-height: 1.6;
		max-width: 80%;
	}
	.date {
		font-size: 85%;
		font-weight: 500;
		margin-bottom: 1.5rem;
	}
	.date span {
		text-transform: uppercase;
	}
	.genres {
		list-style: none;
		padding: 0;
		margin: 0 0 1.5rem;
		display: flex;
		gap: 1rem;
	}
	.genres li {
		border: 2px solid #bbb;
		border-radius: 4rem;
		padding: 0.2rem 1.2rem;
		font-size: 80%;
		text-transform: uppercase;
		font-weight: 500;
		color: #bbb;
	}
</style>
