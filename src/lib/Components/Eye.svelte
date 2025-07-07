<script lang="ts">
	import { onMount } from "svelte";

	let mouseX = $state(0);
	let mouseY = $state(0);

	let angle = $state(0);

	let disabled = $state(false);

	let eye: HTMLDivElement | null = $state(null);

	function handleMouseMove(event: MouseEvent) {
		if (!eye || disabled) return;

		mouseX = event.clientX;
		mouseY = event.clientY;

		const eyeRect = eye.getBoundingClientRect();
		const eyeCenterX = eyeRect.left + eyeRect.width / 2;
		const eyeCenterY = eyeRect.top + eyeRect.height / 2;

		const deltaX = mouseX - eyeCenterX;
		const deltaY = mouseY - eyeCenterY;

		angle = Math.atan2(deltaY, deltaX) * (180 / Math.PI);
		if (angle < 0) {
			angle += 360; // Normalize angle to be between 0 and 360 degrees
		}
	}

	function PokeEye() {
		if (disabled) return;

		disabled = true;

		angle = 90;

		setTimeout(() => {
			disabled = false;
		}, 3000);
	}

	onMount(() => {
		window.addEventListener("mousemove", handleMouseMove);

		return () => {
			window.removeEventListener("mousemove", handleMouseMove);
		};
	});
</script>

<div
	onmouseenter={PokeEye}
	role="button"
	tabindex="0"
	class={`relative rounded-full border border-neutral-800 ${disabled ? "bg-red-300 h-3 mt-3 overflow-y-hidden" : "h-12"} w-12`}
>
	<!-- Actual eye pupil -->
	<div
		bind:this={eye}
		class={`absolute left-1/2 top-1/2 w-full h-6 after:rounded-full after:bg-black after:absolute after:h-6 after:w-6 after:right-1 after:translate-x-1/8`}
		style="transform: translate(-50%, -50%) rotate({angle}deg);"
	></div>
</div>
