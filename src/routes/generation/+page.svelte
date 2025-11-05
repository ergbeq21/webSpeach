<script>
    import { onMount } from "svelte";
	let text = "Hello from Svelte!";
	let voices = [];
	let selectedVoice = null;

	onMount(() => {
		voices = window.speechSynthesis.getVoices();

		window.speechSynthesis.onvoiceschanged = () => {
			voices = window.speechSynthesis.getVoices();
		};
	});

	function speak() {
		if (!text.trim()) return;

		const utterance = new SpeechSynthesisUtterance(text);
		if (selectedVoice) utterance.voice = selectedVoice;
		speechSynthesis.speak(utterance);
	}
</script>

<div class="p-4 space-y-4">
	<textarea bind:value={text} rows="3" class="border p-2 w-full"></textarea>

	<select bind:value={selectedVoice} class="border p-2 w-full">
		<option disabled selected>Select a voice</option>
		{#each voices as v}
			<option value={v}>{v.name} ({v.lang})</option>
		{/each}
	</select>

	<button onclick={speak} class="bg-blue-600 text-white p-2 rounded">Speak</button>
</div>
