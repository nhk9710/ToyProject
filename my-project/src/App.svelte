

<main>
	<h1>{color}</h1> <h2>{name}!</h2>
	<h3>{color} jean</h3>
	<div class="flexy">
		<div class="margins">
			<Fab color="primary" >
				<Icon class="material-icons">favorite</Icon>
			</Fab>
		</div>
	</div>

	<button on:click={changeColor} value="change">update jean color</button>

	<progress value={$progress}></progress>

	<button on:click="{() => progress.set(0)}">
		0%
	</button>

	<button on:click="{() => progress.set(0.25)}">
		25%
	</button>

	<button on:click="{() => progress.set(0.5)}">
		50%
	</button>

	<button on:click="{() => progress.set(0.75)}">
		75%
	</button>

	<button on:click="{() => progress.set(1)}">
		100%
	</button>

</main>

<script lang="ts">
	import Fab, { Icon } from '@smui/fab';
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	});

	export let name;
	let color = 'red';

	const changeColor = () => {
		if(color === 'blue'){
			document.querySelector('h3').style.color='red';
			document.querySelector('h1').style.color='red';
			color = 'red';
		} else{
			document.querySelector('h3').style.color='blue';
			document.querySelector('h1').style.color='red';
			color = 'blue';
		}
	};

</script>

<style>
	main {
		text-align: center;
		width: 100vw;
		height: 100vh;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		background-color: white;
	}

	progress {
		margin: 0 auto;
		display: block;
		width: 70%;
	}

	h1 {

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