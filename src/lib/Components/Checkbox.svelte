<script lang="ts">
	let checked = $state(false);

	function handleCheck() {
		let confirmation = confirm(
			"This action will have consequences. Are you sure?"
		);

		if (confirmation) {
			alert("What are you doing here? You didn't try to check this box.");
		} else {
			alert("Good!");
		}

		checked = false;
	}
</script>

<div class="absolute m-24">
	<label class="flex items-center">
		<input
			type="checkbox"
			bind:checked
			onchange={handleCheck}
			class="form-checkbox h-5 w-5 text-blue-600 border-gray-300 rounded focus:ring-blue-500"
		/>
		<span class="ml-2 text-gray-700">Check me!</span>
	</label>
</div>
