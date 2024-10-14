<script lang="ts">
	import { Download } from 'lucide-svelte';
	import { DarkMode } from '$lib/components/store';
	import { InfoText } from '$lib/components/store';
</script>

<div
	class="container border-dashed border-gray-600 border-2 p-6 h-2/3 flex items-center justify-center rounded-xl dark:border-white"
>
	<div class="items-center row-auto justify-center text-center">
		<p
			class="text-6xl font-bold text-transparent bg-clip-text bg-gradient-to-tr from-yellow-400 via-pink-700 to-pink-400"
		>
			Paste to download
		</p>
		{#if $InfoText}
			<p class="text-black text-xl mt-4 dark:text-white">
				Easily download images directly from your clipboard with this simple tool.
			</p>
			<p class="text-black text-xl mt-4 dark:text-white">
				This project is open source. The code can be viewed at
				<a class="underline" href="https://github.com/Lukas-Siegle/paste-to-download">Github</a>
			</p>
		{/if}
		<p class="text-black text-center mt-4 dark:text-white">
			Use <strong>CTRL + V</strong> to paste
		</p>

		<div class="flex justify-center mt-4 dark:text-white">
			<Download size={48} color={$DarkMode ? '#ffffff' : '#000000'} />
		</div>
	</div>
</div>
