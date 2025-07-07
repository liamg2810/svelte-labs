<script lang="ts">
	import { onMount } from "svelte";

	let checked = $state(false);

	function RandomCheck() {
		setTimeout(
			() => {
				checked = Boolean(Math.round(Math.random()));
				RandomCheck();
			},
			Math.random() * 5000 + 1000
		);
	}

	onMount(() => {
		RandomCheck();
	});
</script>

<input
	type="checkbox"
	bind:checked
	class="absolute left-1/2 top-1/2 -translate-1/2 form-checkbox h-8 w-8 text-blue-600 border-gray-300 rounded focus:ring-blue-500"
/>
