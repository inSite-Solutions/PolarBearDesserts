<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import { scrollY } from 'svelte/reactivity/window';

	let open = $state(false);
</script>

<!-- you can ignore the scrollY undefined error -->
<nav class="sticky top-0 left-0 z-50 w-full">
	<div
		class={`bg-secondary w-full transition-all duration-300 
    ${scrollY.current && scrollY.current > 50 ? 'opacity-80' : 'opacity-100'}`}
	>
		<div class="flex w-full items-center justify-between px-3">
			<img class="h-auto w-[20vw]" src="/images/logo.png" alt="Logo" />
			<div class="absolute left-1/2 -translate-x-1/2">
				<img class="h-auto w-[50vw]" src="/images/logoText.png" alt="Logo Text" />
			</div>
			<button onclick={() => (open = !open)} aria-label="open navigation menu">
				<img src="/icons/Menu.png" alt="" class="h-auto w-[10vw]" />
			</button>
		</div>
	</div>

	{#if open}
		<div class="fixed inset-0 z-40 flex">
			<button
				class="absolute h-full w-[100%] bg-gray-500/40"
				onclick={() => (open = false)}
				aria-label="close navigation menu"
				transition:fade={{ duration: 500 }}
			></button>
			<div
				class="bg-secondary absolute right-0 flex h-full w-[70%] flex-col pt-5"
				transition:fly={{ x: 100, duration: 500 }}
			>
				<button
					class="absolute right-[5%] z-50"
					onclick={() => (open = false)}
					aria-label="open navigation menu"
				>
					<img src="/icons/Close.png" alt="" class="h-auto w-[8vw]" />
				</button>
				<div class="absolute flex h-full w-full flex-col items-center gap-3 pt-10">
					<a href="/" class="text-2xl" onclick={() => (open = false)}>Home</a>
					<hr class="w-[90%] opacity-30" />
					<a href="/menu" class="text-2xl" onclick={() => (open = false)}>Menu</a>
					<hr class="w-[90%] opacity-30" />
					<a href="/about" class="text-2xl" onclick={() => (open = false)}>About</a>
				</div>
			</div>
		</div>
	{/if}
</nav>
