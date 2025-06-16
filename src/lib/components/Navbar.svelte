<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import { scrollY } from 'svelte/reactivity/window';

	let open = $state(false);
</script>


<div class="absolute inset-0 z-0 h-[133px] w-full">
		<div class="bg-primary h-full w-full"></div>
		<div
			class="pointer-events-none absolute inset-0 bg-[url('/images/grain.png')] bg-repeat opacity-25"
		></div>
</div>

<nav class="sticky top-0 left-0 z-50 w-full">
		<!-- Iceberg Background Wrapper -->
	<div
		class={`relative h-[133px] w-full transition-all duration-300 
    ${scrollY.current && scrollY.current > 50 ? 'opacity-80' : 'opacity-100'}`}
	>
		<!-- Iceberg SVG -->
		<svg
			class="pointer-events-none absolute inset-0 z-0 h-full w-full"
			viewBox="0 0 1233 163"
			xmlns="http://www.w3.org/2000/svg"
			preserveAspectRatio="none"
		>
			<path
				fill="#fafafa"
				style={`filter: drop-shadow(0 4px 6px rgba(0, 0, 0, ${
					scrollY.current && scrollY.current > 50 ? '0.15' : '0.1'
				}))`}
				d="M0,0 H1233 V80 L1232,119 L1208,104 L1150,147 L1072,98 L1012,142 L936,108 L868,152 L806,102 L738,144 L666,112 L610,151 L552,105 L478,147 L410,103 L350,137 L282,86 L236,140 L160,100 L108,136 L34,103 L0,162 Z"
			/>
		</svg>

		<!-- Navbar Content -->
		<div class="absolute top-0 left-0 z-10 flex w-full items-center justify-between px-4 pt-4">
			<img class="h-auto w-[20vw]" src="/images/logo.png" alt="Logo" />
			<div class="absolute top-4 left-1/2 -translate-x-1/2">
				<img class="h-auto w-[50vw]" src="/images/logoText.png" alt="Logo Text" />
			</div>
			<button onclick={() => (open = !open)} aria-label="open navigation menu">
				<img src="/icons/Menu.png" alt="Menu" class="h-auto w-[10vw]" />
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
					aria-label="close navigation menu"
				>
					<img src="/icons/Close.png" alt="" class="h-auto w-[8vw]" />
				</button>
				<div class="absolute flex h-full w-full flex-col items-center gap-10 pt-10">
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
