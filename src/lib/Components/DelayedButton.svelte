<script lang="ts">
	import { onMount } from "svelte";

	const delay = 3000; // 3 seconds

	let debounce = $state(false);

	let ypos = $state(0);

	let hidden = $state(true);

	function handleClick() {
		if (debounce) return;

		debounce = true;

		setTimeout(() => {
			ypos -= 50;
			debounce = false;
		}, delay);
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
