<script>
  import Form from './Input.svelte';
  import Dash from './Pool.svelte';

	export let name;
</script>

<main>
  <p id='greeting'>Welcome</p>
  <p id='fragment'>to the</p>
	<h1>Tall grass</h1>
  <hr />
  <Form />
  <Dash />
</main>

<style>
	main {
    font-family: 'Courier New', monospace;
		max-width: 240px;
		margin: 0 auto;
		padding: 1em;
		text-align: center;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
    margin: .1em;
    text-shadow: 2px 4px 6px #8f8f9d;
		text-transform: uppercase;
	}

  hr {
		color: #ff3e00;
    width: 70%;
  }

  p#greeting {
    font-size: 1.7em;
    letter-spacing: 1em;
    margin: 0;
    text-transform: uppercase;
  }

  p#fragment {
    font-size: .8em;
    margin: 1em 0 0;
  }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
