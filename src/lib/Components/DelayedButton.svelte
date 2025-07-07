<script lang="ts">
	import { onMount } from "svelte";

	const delay = 3000; // 3 seconds

	let debounce = $state(false);

	let ypos = $state(0);

	let crocodiloX = $state(-100);
	let nukeY = $state(0);

	let dropNuke = $state(false);
	let hidden = $state(true);
	let explosion = $state(false);

	function handleClick() {
		if (debounce) return;

		debounce = true;

		setTimeout(() => {
			explosion = true;
			setTimeout(() => {
				crocodiloX = window.innerWidth / 2 + 100; // Center the crocodilo
				nukeY = window.innerHeight / 2 - 100; // Center the nuke
				setTimeout(() => {
					dropNuke = true;

					setTimeout(() => {
						nukeY = window.innerHeight - 50;
						crocodiloX = -100;

						setTimeout(() => {
							dropNuke = false;
							hidden = true;
							explosion = false;
							debounce = false;
						}, 2000);
					}, 1000);
				}, 1000);
			}, 1000);
		}, 0);
	}

	onMount(() => {
		ypos = window.innerHeight - 50;
		hidden = false;
	});
</script>

{#if !hidden}
	<button
		class="absolute left-1/2 bg-red-500 border border-red-800 transition-all duration-75 rounded-lg p-2 cursor-pointer"
		style={`transform: translate(-50%, ${ypos}px);`}
		onclick={handleClick}
	>
		Click Me (I wont move I promise)
	</button>
{/if}
{#if explosion}
	<img
		src="https://brainrottoys.com/cdn/shop/files/Bombardino_Crocodilo_Toy_Viral_Italian_Brainrot_Meme_Collectible..png?v=1745917965&width=1426"
		alt="Crocodilo"
		class="absolute top-1/2 -translate-y-1/2 w-24 h-24 z-20 transition-transform duration-1000"
		style={`transform: translateX(${crocodiloX}px);`}
	/>
	{#if dropNuke}
		<img
			src="https://gifdb.com/images/thumbnail/activate-nuke-explosion-moj9v9r4xvui2xri.gif"
			alt="Nuke Explosion"
			class="absolute left-1/2 -translate-x-1/2 transition-transform duration-1000 aspect-square w-12 object-cover z-10"
			style={`transform: translateY(${nukeY}px);`}
		/>
	{/if}
{/if}
