<script lang="ts">
	import { fade } from 'svelte/transition';

	let laugh = '';
	let alert = false;
</script>

<svelte:head>
	<title>Psycho laugh generator</title>
</svelte:head>

<div class="mx-4">
	<div
		class="mx-auto my-32 flex max-w-prose flex-col gap-4 rounded-md bg-pink-400 p-8 shadow-md shadow-pink-400"
	>
		<h1
			class="relative font-cursive text-4xl after:absolute after:-bottom-2 after:left-0 after:h-6 after:w-full after:rounded-md after:bg-purple-200 after:opacity-40 after:content-['']"
		>
			Psycho Laugh Generator
		</h1>
		{#if laugh}
			<button
				class="break-all rounded-lg bg-purple-200 p-4 text-center font-mono text-lg"
				on:click={() => {
					const input = document.createElement('input');
					input.value = laugh;
					document.body.appendChild(input);
					input.select();
					document.execCommand('copy');
					input.remove();
					alert = true;
					setTimeout(() => {
						alert = false;
					}, 2000);
				}}
			>
				&nbsp;{laugh}
			</button>
		{:else}
			<p class="p-4 font-mono text-lg">&nbsp;</p>
		{/if}
		<button
			class="touch-manipulation rounded-md bg-white px-4 py-2"
			on:click={() => {
				laugh = 'AHAHAH';
				const glyphCount = 5 + Math.floor(Math.random() * 5);
				for (let i = 0; i < glyphCount; i++) {
					const ays = Math.floor(Math.random() * 2) + 1;
					const aches = Math.floor(Math.random() * 2) + 1;
					laugh += `${'A'.repeat(ays)}${'H'.repeat(aches)}`;
				}
				const trailingAys = Math.floor(Math.random() * 3);
				laugh += 'A'.repeat(trailingAys);
			}}
		>
			Generate ✨
		</button>
	</div>
</div>

{#if alert}
	<div
		transition:fade
		class="fixed bottom-4 left-4 right-4 rounded-md bg-purple-200 p-4 shadow-md shadow-purple-200"
	>
		Copied to clipboard
	</div>
{/if}
