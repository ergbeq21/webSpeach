<script>
	import { Mic, Volume2 } from "lucide-svelte";
</script>

<div class="min-h-screen flex flex-col items-center justify-center bg-linear-to-br from-indigo-100 via-blue-50 to-sky-100 text-gray-800">
	<h1 class="text-5xl font-bold mb-4">Web Speech Playground</h1>
	<p class="mb-12 text-lg text-gray-600 text-center max-w-lg">
		Experience live <strong>speech recognition</strong> and <strong>speech synthesis</strong> right in your browser.
	</p>

	<div class="flex flex-col sm:flex-row gap-8">
		<a href="/generation"
			class="group w-64 bg-white/80 backdrop-blur-xl p-6 rounded-2xl shadow-lg hover:shadow-xl border border-blue-100 transition transform hover:-translate-y-1">
			<div class="flex items-center space-x-3 mb-3">
				<Volume2 class="w-6 h-6 text-blue-600 group-hover:text-blue-700" />
				<h2 class="text-xl font-semibold text-blue-700 group-hover:text-blue-800">
					Text to Speech
				</h2>
			</div>
			<p class="text-gray-600 text-sm">
				Type something and let your browser speak it out loud.
			</p>
		</a>

		<a href="/recognition"
			class="group w-64 bg-white/80 backdrop-blur-xl p-6 rounded-2xl shadow-lg hover:shadow-xl border border-green-100 transition transform hover:-translate-y-1">
			<div class="flex items-center space-x-3 mb-3">
				<Mic class="w-6 h-6 text-green-600 group-hover:text-green-700" />
				<h2 class="text-xl font-semibold text-green-700 group-hover:text-green-800">
					Speech to Text
				</h2>
			</div>
			<p class="text-gray-600 text-sm">
				Speak and see your words instantly turned into text.
			</p>
		</a>
	</div>
</div>
