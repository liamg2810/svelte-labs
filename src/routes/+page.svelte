<script>
	import Checkbox from "$lib/Components/Checkbox.svelte";
	import DelayedButton from "$lib/Components/DelayedButton.svelte";
	import Eye from "$lib/Components/Eye.svelte";
	import Mood from "$lib/Components/Mood.svelte";
	import NothingButton from "$lib/Components/NothingButton.svelte";
	import RunningButton from "$lib/Components/RunningButton.svelte";
</script>

<div class="absolute w-full text-center mt-10 font-bold text-5xl">
	Svelte Labs
</div>

<RunningButton />
<Checkbox />
<Mood />
<DelayedButton />
<NothingButton />
<div class="absolute m-5">
	<Eye />
</div>
<div class="absolute ml-32 m-5">
	<Eye />
</div>
