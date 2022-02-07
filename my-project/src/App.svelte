<div class="wrap">
<header>
	<b>This is Svelte World!</b>
</header>

<main>
	<!-- color switching -->
	<h1>{color}</h1> <h2>{name}!</h2>
	<h3>{color} jean</h3>


	<!-- progress bar -->
	<div class="middle-bar">
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

	<div class="flex-table">
		<div>
			{#if count < 31}
			<button on:click={handleClick}>
				눌러보세요! ====>
			</button>
				{:else if 30 <= count}
				<button disabled>
					고만눌러 ㅋㅋ;
				</button>
			{/if}
		</div>
		<div>
			{#if count < 20}
				<h5 style="color: white">당신의 클릭수는?</h5>
				<p>{count}</p>
				{:else if 21 <= count }
				<p>진짜 열심히 누르네 ㅋㅋ;</p>
			{/if}
		</div>
	</div>
	<div>
		{#if 30 <= count}
		<img src="https://item.kakaocdn.net/do/3727c16c143eb219d7b32939d9886113f604e7b0e6900f9ac53a43965300eb9a">
		{/if}
	</div>

	<div>
		<h3 class="lucktext">오늘의 운세</h3>
		<Randomizer list={list} class="lucky"/>
	</div>

	<div class="randomProduct">
		<div>
			<h1><span style="color: #3eff13">랜</span><span style="color: rebeccapurple">덤</span><span style="color: deepskyblue">뽑</span><span style="color: #ff7825">기</span></h1>
			<p>소지금 : {money}원</p>
		</div>
		<button class="getProduct" on:click={gotchaProduct}>+</button>

		<p>뽑기 아이템: {item}</p>
	</div>

</main>
</div>



<!-- =========================================================================================================== -->
<script lang="ts">
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';
	import { fade } from 'svelte/transition';
	import Randomizer from './Randomizer.svelte';

	/*==============random=================================*/
	let list=[
		{item:'오늘은 대길!!', id: 1},
		{item:'오늘은 대흉!!!', id: 2},
		{item:'페이지 주인장 밥사주기!!', id: 3},
		{item:'길가다 100원 줍는 날!!', id: 4},
		{item:'재수 없는 날!!', id: 5},
		{item:'뭔가 뭔가 일어나는 날!!', id: 6},
		{item:'배가 많이 고파지는 날!!', id: 7},
		{item:'페이지 주인 실력에 감탄하는 날!!', id: 8},
		{item:'조용히 지나가는 날!!', id: 9},
		{item:'아이유 좋은날!!', id: 10},

	];

	let product=[
		{item:'또래오래 양념치킨', id: 1},
		{item:'돋보기 안경', id: 2},
		{item:'헌 옷', id: 3},
		{item:'노호관 명함', id: 4},
		{item:'무신사 스탠다드', id: 5},
		{item:'고오급 마우스', id: 6},
		{item:'맥북', id: 7},
		{item:'일회용 마스크', id: 8},
		{item:'낡은 키보드', id: 9},
		{item:'전설급 츄르', id: 10},

	]

	/*=====================================================*/

	const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	});

	export let name;
	let color = 'red';
	let visible = true;
	let money = 1000;

	let count = 0;

	let item = '';

	function handleClick() {
		count += 1;
	}

	const gotchaProduct = (e) => {
		e.preventDefault();
		/*item = product[Math.floor(Math.random() * product.length)].item.toUpperCase();
		if (money != 0){
			money -= 200;
		}
		else if (money == 0){
			alert('돈을 다썼어요~')
		}*/
		alert('개발중이다에요~ 좋은아이디어 있으면 알려달라에요~')
	}


	const changeColor = () => {
		if(color === 'blue'){
			document.querySelector('h3').style.color='red';
			document.querySelector('h1').style.color='red';
			color = 'red';
		} else{
			document.querySelector('h3').style.color='blue';
			document.querySelector('h1').style.color='blue';
			color = 'blue';
		}
	};

</script>

<style>
	header{
		background-color: #ff7825;
		text-align: center;
		font-size: 4em;
		color: white;
	}

	main {
		width: 100vw;
		text-align: center;
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

	.middle-bar{
		background-color: #666666;
	}

	.flex-table{
		margin: 0 auto;
		max-width: 80%;
		display: flex;
		justify-content: space-between;
		background-color: #3eff13;
		padding: 10px;
		border-radius: 10px;
	}
	.lucktext{
		font-size: 3em;
		margin-bottom: 20px;
	}

	.wrap{
		width: 100%;
		height: 100%;
	}

	.randomProduct{ margin-top: 30px; border-top: 2px solid #ff7825 }
	.randomProduct div h1{ font-weight: bolder; }

	.getProduct{ background: #ff7825; color: white; padding: 10px; font-size: 2em; font-weight: bolder; border: 1px solid #ff7825; border-radius: 100px; cursor: pointer }
	.getProduct:hover{ transition: all 0.3s; transform: rotate(360deg) }
</style>