<script>
	import Input from "./components/Input.svelte";
	import Result from "./components/Result.svelte";
	import Search from "./components/Search.svelte";

	const ToggleDark = () => {
		window.document.body.classList.toggle("dark-mode");
	};

	$: {
		ToggleDark();
	}
	let movie_name,
		result,
		error = false;
</script>

<style>
	:global(body) {
		background-color: #fff;
		color: #000;
	}

	:global(body.dark-mode) {
		background-color: #000;
		color: #fff;
	}

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		font-size: 4em;
		color: #ff3e00;
		text-transform: uppercase;
		font-weight: 100;
	}

	:global(body.dark-mode) h1 {
		color: #fff;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.toggle__mode {
		position: absolute;
		top: 20px;
		right: 20px;
	}

	.search__text {
		display: inline;
		background-color: #ff3e00;
		color: #fff;
		padding: 0 10px;
	}
</style>

<main>
	<h1>
		Movie
		<div class="search__text">Search</div>
	</h1>
	<button on:click={ToggleDark} class="toggle__mode" />
	<Input
		on:MOVIE_NAME={({ detail }) => {
			movie_name = detail;
			error = false;
		}} />
	<Search
		movie={movie_name}
		on:result={({ detail }) => (result = detail)}
		on:not_found={({ detail }) => (error = detail)} />
	{#if result && !error}
		<Result data={result} />
	{:else if error != false}
		<p>{error}</p>
	{/if}
</main>
