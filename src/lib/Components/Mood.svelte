<script lang="ts">
	const moods: { percent: number; mood: string }[] = [
		{ percent: 0, mood: "💼" },
		{ percent: 0.2, mood: "🎟️" },
		{ percent: 0.4, mood: "🥀" },
		{ percent: 0.6, mood: "😝" },
		{ percent: 0.8, mood: "🤬" },
		{ percent: 1, mood: "⛽" },
	];

	let currentMood = $state(0);
</script>

<div class="absolute right-0 m-64">
	<div class="flex flex-col">
		<label for="mood" class="mb-2 text-gray-700 text-lg font-bold">
			Mood: {moods.find((val) => val.percent === currentMood)
				?.mood}</label
		>
		<input
			id="mood"
			type="range"
			min="0"
			max="1"
			step="0.2"
			bind:value={currentMood}
			class="w-64 mb-4"
		/>
	</div>
</div>
