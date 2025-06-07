<script lang="ts">
	import { fly } from 'svelte/transition';
	import { scrollY } from 'svelte/reactivity/window';

	let open = $state(false);
</script>

<!-- you can ignore the scrollY undefined error -->
<nav class="sticky top-0 left-0 z-50 w-full">
	<div
		class={`bg-secondary w-full transition-all duration-300 
    ${scrollY.current > 50 ? 'opacity-80 shadow-lg' : 'opacity-100'}`}
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
		<div class="fixed inset-0 z-40 flex" transition:fly={{ x: 100, duration: 500 }}>
			<button
				class="h-full w-[30%]"
				onclick={() => (open = false)}
				aria-label="close navigation menu"
			></button>
			<div class="flex h-full w-[70%] flex-col items-center gap-3 bg-gray-500/90 pt-5">
				<a href="/" class="text-secondary text-2xl" onclick={() => (open = false)}>Home</a>
				<a href="/menu" class="text-secondary text-2xl" onclick={() => (open = false)}>Menu</a>
				<a href="/about" class="text-secondary text-2xl" onclick={() => (open = false)}>About</a>
			</div>
		</div>
	{/if}
</nav>
