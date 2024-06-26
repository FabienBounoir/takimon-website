<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';

	const totalTakimon = 125;
	const totalTypes = 5;

	const type = ['Feu', 'Eau', 'Plante', 'Shiny', 'Ténèbre'];
</script>

<svelte:head>
	<title>Takimon</title>
</svelte:head>

<section>
	{#each { length: totalTakimon } as _, i}
		{#each { length: totalTypes } as _, j}
			<div>
				{#if j === 0}
					<p class="id">
						#{i + 1}
					</p>
				{/if}
				<img
					src={`https://cdn.takimon.com/image.php?id=${i + 1}&element=${j + 1}`}
					alt={`Takimon ${i + 1} of type ${j + 1}`}
				/>
				<img class="type" src={`${j + 1}.webp`} />
				<p></p>
			</div>
		{/each}
	{/each}
</section>
```

<style>
	section {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		gap: 3px;
		width: 100vw;
	}

	section > div {
		position: relative;
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	img.type {
		position: absolute;
		bottom: 0rem;
		right: 0rem;
		color: white;
		margin: 0;
		padding: 0rem;
		width: 2rem;
		height: 2rem;
	}

	p.id {
		position: absolute;
		top: 3px;
		left: 3px;
		color: white;
		margin: 0;
		padding: 0px;
		font-size: 1.2rem;
		line-height: 18px;
		font-weight: 500;
		font-family: 'Roboto', sans-serif;
	}
</style>
