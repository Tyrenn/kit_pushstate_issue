<script>
	import {pushState} from '$app/navigation';
	import { page } from '$app/stores';

	let showSquare = false;

	function onChangeState(state){
		console.log("change state", state)
		if(state?.show)
			showSquare = true;
		else
			showSquare = false;
	}

	function onShow(){
		pushState('/square', {show : true});
	}

	function onHide(){
		pushState('/', {show : false});
	}

	$ : onChangeState($page.state)
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<svelte:window on:popstate={() => console.log('Popping state')} />

<section>
	<button on:click={onShow}>Show Square</button>
	<button on:click={onHide}>Hide Square</button>


	{#if showSquare}
		<div class="square"/>
	{/if}

</section>

<style>

	.square{
		width: 40px;
		height: 40px;
		background-color: red;
		margin-top: 20px;
	}

</style>
