<script>
	export let name;
	// let showCount;
	import "../node_modules/bootstrap/dist/css/bootstrap.min.css";
	// import "../node_modules/bootstrap/dist/js/bootstrap.min.js";
	import WordsAndInput from "./WordsAndInput.svelte";
	import Offcanvas from "./offcanvasMenu.svelte";

	const pkg = {
		hint:'Type to Start'
	};

	function callAlert() {
		alert("Nope!");
	}
</script>


<main>
	
	<Offcanvas></Offcanvas>
	<h1 class="mb-5">Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial" on:click|preventDefault={callAlert}>Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<WordsAndInput {...pkg}></WordsAndInput>
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