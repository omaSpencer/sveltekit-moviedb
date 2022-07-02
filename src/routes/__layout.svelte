<script>
	import '../global.css';
</script>

<svelte:head>
	<title>Movie DB</title>
</svelte:head>

<nav>
	<ul>
		<li>
			<a href="/">Home</a>
		</li>
	</ul>
</nav>
<slot><!-- optional fallback --></slot>

<style>
	nav {
		max-width: 1280px;
		margin: 0 auto;
		padding: 20px;
	}
	ul {
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		gap: 1rem;
	}
	a,
	a:visited,
	a:hover,
	a:link {
		text-decoration: none;
		color: #333;
	}
</style>
