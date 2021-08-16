<script>
	export let name;
	let say ='what!? GGGG';
	let test = 'fkf';
	import Timer from "./timer.svelte";
	import "../node_modules/bootstrap/dist/css/bootstrap.min.css";
</script>


<main>
	<h1 class="mb-5">Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<h2>{say}</h2>
	<Timer></Timer>
</main>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}


	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>