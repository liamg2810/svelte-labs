<script lang="ts">
	import { onMount } from "svelte";

	let randomness = $state(200);

	let x = $state(randomness);
	let y = $state(randomness);

	let failed = $state(0);

	function handleOnEnter(ev: MouseEvent) {
		const randomX = Math.random() + 1;
		const randomY = Math.random() + 1;

		const newX = Math.max(
			randomness,
			ev.clientX + (randomX < 1.5 ? -randomX : randomX) * randomness
		);
		const newY = Math.max(
			randomness,
			ev.clientY + (randomY < 1.5 ? -randomY : randomY) * randomness
		);

		x = Math.min(Math.max(0, newX), window.innerWidth - randomness - 100);
		y = Math.min(Math.max(0, newY), window.innerHeight - randomness - 100);

		failed++;

		randomness++;
	}

	function onClick() {
		alert("Impossible...");
		window.close();
	}

	onMount(() => {
		x = Math.max(
			randomness,
			Math.random() * window.innerWidth - randomness - 100
		);
		y = Math.max(
			randomness,
			Math.random() * window.innerHeight - randomness - 100
		);
	});
</script>

<button
	onmouseenter={handleOnEnter}
	class="absolute bg-blue-500 border border-blue-800 rounded-lg p-2 cursor-pointer"
	style={`transform: translate(${x}px, ${y}px);`}
	onclick={onClick}
	>Click Me{#if failed > 0}<br />Failed attempts {failed}{/if}</button
>
