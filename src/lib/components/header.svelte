<script lang="ts">
	import { onMount } from 'svelte';
	import { Github, Sun, Moon, Info, Home } from 'lucide-svelte';
	import { DarkMode, InfoText } from './store';
	onMount(() => {
		if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
			toggleDarkMode();
		}
	});

	function toggleDarkMode() {
		DarkMode.set(!$DarkMode);
		if ($DarkMode) {
			document.documentElement.classList.add('dark');
		} else {
			document.documentElement.classList.remove('dark');
		}
	}

</script>

<div
	class="p-5 flex flex-row content-center justify-center rounded-lg border border-solid border-gray-200 mb-2 bg-slate-100  dark:text-white dark:border-slate-950 w-fit dark:bg-zinc-900"
>
	<button on:click={toggleDarkMode} class="pr-2">
		{#if DarkMode}
			<Sun size={32} color={$DarkMode ? '#ffffff' : '#000000'} />
		{:else}
			<Moon size={32} color={$DarkMode ? '#ffffff' : '#000000'} />
		{/if}
	</button>
	<a class="pl-2 pr-2" href="https://github.com/Lukas-Siegle/paste-to-download">
		<Github size={32} color={$DarkMode ? '#ffffff' : '#000000'} />
	</a>
	<button class="pl-2" on:click={() => InfoText.set(!$InfoText)}>
		<Info size={32} color={$DarkMode ? '#ffffff' : '#000000'}/>
	</button>	

</div>
