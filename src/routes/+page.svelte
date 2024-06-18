<script lang="ts">
	let laugh = '';
</script>

<div
	class="mx-auto mx-4 my-32 max-w-prose bg-pink-400 shadow-md shadow-pink-400 rounded-md p-8 flex flex-col gap-4"
>
	<h1 class="text-4xl font-cursive relative after:content-[''] after:absolute after:left-0 after:-bottom-2 after:w-full after:h-6 after:bg-purple-200 after:opacity-40 after:rounded-md">Psycho Laugh Generator</h1>
	{#if laugh}
		<p class="text-center p-4 rounded-lg bg-purple-200 font-mono text-lg break-all">&nbsp;{laugh}</p>
	{:else}
		<p class="p-4 text-lg font-mono">&nbsp;</p>
	{/if}
	<button
		class="bg-white py-2 px-4 rounded-md"
		on:click={() => {
			laugh = 'AHAHAH';
			const glyphCount = 5 + Math.floor(Math.random() * 5);
			for (let i = 0; i < glyphCount; i++) {
				const ays = Math.floor(Math.random() * 2) + 1;
				const aches = Math.floor(Math.random() * 2) + 1;
				laugh += `${'A'.repeat(ays)}${'H'.repeat(aches)}`;
			}
			const trailingAches = Math.floor(Math.random() * 3);
			laugh += 'H'.repeat(trailingAches);
		}}
	>
		Generate ✨
	</button>
</div>
