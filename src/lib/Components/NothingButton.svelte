<script lang="ts">
	let clicks = $state(0);

	function handleClick() {
		clicks++;

		if (clicks === 30) {
			alert("I said stop clicking! Now you die.");
			window.location.href =
				"https://www.youtube.com/watch?v=dQw4w9WgXcQ";
		} else if (clicks === 20) {
			alert("If you wont heed my warning, I will have to take action.");
		} else if (clicks === 10) {
			alert("Do you mind? I'm sleeping here! Stop clicking me!");
		}
	}
</script>

{#if clicks < 30}
	<button
		onclick={handleClick}
		class="absolute right-0 bottom-0 m-96 cursor-pointer p-2 rounded-lg border-purple-700 border bg-purple-500 hover:bg-purple-700 transition-colors"
		>{#if clicks >= 20}🤬{:else if clicks >= 10}😤{:else}😴{/if}</button
	>
{/if}
