

<main>
	<h1>{color} {name}!</h1>
	<h3>{color} jean</h3>
	<div class="flexy">
		<div class="margins">
			<Fab color="primary" >
				<Icon class="material-icons">favorite</Icon>
			</Fab>
		</div>
	</div>

	<button on:click={changeColor} value="change">update jean color</button>


</main>

<script lang="ts">
	import Fab, { Icon } from '@smui/fab';
	import Badge from '@smui-extra/badge';

	export let name;
	let color = 'red';

	const changeColor = () => {
		if(color === 'blue'){
			document.querySelector('h3').style.color='red';
			color = 'red';
		} else{
			document.querySelector('h3').style.color='blue';
			color = 'blue';
		}
	};

</script>

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