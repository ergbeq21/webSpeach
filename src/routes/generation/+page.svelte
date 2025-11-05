<script>
	import { onMount } from "svelte";
	import { ArrowLeft, Volume2, MessageSquare } from "lucide-svelte";

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

	function goBack() {
		history.back();
	}
</script>

<div class="min-h-screen flex flex-col items-center justify-center bg-linear-to-br from-blue-500 via-purple-500 to-pink-500 p-6 text-gray-800">
	<!-- Container Card -->
	<div class="w-full max-w-md bg-white/90 backdrop-blur-md rounded-3xl shadow-xl p-6 space-y-6 border border-white/30">

		<!-- Go Back -->
		<button
			onclick={goBack}
			class="flex cursor-pointer items-center gap-2 text-blue-600 hover:text-blue-800 transition-colors"
		>
			<ArrowLeft size={20} /> <span class="font-medium">Go Back</span>
		</button>

		<!-- Header -->
		<div class="text-center">
			<h1 class="text-3xl font-bold text-gray-800 flex justify-center items-center gap-2">
				<MessageSquare class="text-blue-600" size={28} />
				Text to Speech
			</h1>
			<p class="text-gray-500 mt-1 text-sm">Write something and let your browser speak it aloud</p>
		</div>

		<!-- Text Area -->
		<textarea
			bind:value={text}
			rows="4"
			class="w-full border border-gray-300 rounded-xl p-3 text-gray-700 focus:outline-none focus:ring-2 focus:ring-blue-500 placeholder:text-gray-400 resize-none"
			placeholder="Type something to speak..."
		></textarea>

		<!-- Voice Select -->
		<select
			bind:value={selectedVoice}
			class="w-full border border-gray-300 rounded-xl p-3 text-gray-700 focus:outline-none focus:ring-2 focus:ring-blue-500"
		>
			<option disabled selected>Select a voice</option>
			{#each voices as v}
				<option value={v}>{v.name} ({v.lang})</option>
			{/each}
		</select>

		<!-- Speak Button -->
		<button
			onclick={speak}
			class="flex items-center justify-center gap-2 w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 rounded-xl transition-all shadow-md hover:shadow-lg"
		>
			<Volume2 size={22} /> Speak
		</button>
	</div>

	<!-- Footer -->
	<p class="text-white/80 mt-8 text-sm">Powered by the Web Speech API</p>
</div>
