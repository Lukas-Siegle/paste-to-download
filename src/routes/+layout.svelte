<script lang="ts">
	import '../app.css';
	import Header from '$lib/components/header.svelte';
	let imageUrl = '';

	function handlePaste(event: ClipboardEvent) {
		const clipboardItems = event.clipboardData?.items;

		if (!clipboardItems) return;

		for (let i = 0; i < clipboardItems.length; i++) {
			const item = clipboardItems[i];
			if (item.type.indexOf('image') === 0) {
				const file = item.getAsFile();
				if (file) {
					const reader = new FileReader();

					reader.onload = function (event: ProgressEvent<FileReader>) {
						imageUrl = event.target?.result as string;
						downloadImage();
					};
					reader.readAsDataURL(file);
				}
			}
		}
	}

	function downloadImage() {
		if (imageUrl) {
			const link = document.createElement('a');
			link.href = imageUrl;
			link.download = 'pasted-image.png';
			link.click();
		}
	}
</script>

<div on:paste={handlePaste}>
	<div
		class="h-screen flex flex-col justify-center content-center items-center bg-zinc-100 dark:bg-zinc-950"
	>
		<Header></Header>
		<slot />
	</div>
</div>
