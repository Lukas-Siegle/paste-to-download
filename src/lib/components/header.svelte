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
	class="p-5 flex flex-row content-center justify-center rounded-lg dark:text-white dark:border-slate-950 w-fit dark "
>
	<button on:click={toggleDarkMode} class="pr-2">
		{#if DarkMode}
			<Sun size={34} color={$DarkMode ? '#ffffff' : '#000000'} />
		{:else}
			<Moon size={34} color={$DarkMode ? '#ffffff' : '#000000'} />
		{/if}
	</button>
	<a class="pl-4 pr-4" href="https://github.com/Lukas-Siegle/paste-to-download">
		<Github size={34} color={$DarkMode ? '#ffffff' : '#000000'} />
	</a>
	<button class="pl-2" on:click={() => InfoText.set(!$InfoText)}>
		<Info size={34} color={$DarkMode ? '#ffffff' : '#000000'}/>
	</button>	

</div>
