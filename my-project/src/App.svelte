

<main>
	<!-- color switching -->
	<h1>{color}</h1> <h2>{name}!</h2>
	<h3>{color} jean</h3>
	<div class="flexy">
		<div class="margins">
			<Fab color="primary" >
				<Icon class="material-icons">favorite</Icon>
			</Fab>
		</div>
	</div>

	<!-- progress bar -->
	<div>
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
	</div>

	<label>
		<input type="checkbox" bind:checked={visible}>
		사라지는 버튼
	</label>

	{#if visible}
		<img transition:fade style="width: 100px; height: 100px" src="https://w.namu.la/s/0c6301df01fc4f180ec65717bad3d0254258abf0be33299e55df7c261040f517518eb9008a1a2cd3d7b8b7777d70182c185bc891b1054dc57b11cc46fd29130a3474f1b75b816024dfdc16b692a0c77c" alt="뚱이 없다.." />
	{/if}
</main>



<script lang="ts">
	import Fab, { Icon } from '@smui/fab';
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';
	import { fade } from 'svelte/transition';

	const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	});

	export let name;
	let color = 'red';
	let visible = true;

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
		padding: 1em;
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
			max-width: 100%;
		}
	}
</style>