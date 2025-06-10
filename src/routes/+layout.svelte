<script lang="ts">
	import '../app.css';
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { scrollY } from 'svelte/reactivity/window';
	let { children } = $props();
</script>

<Navbar />
<main class="bg-primary relative">
	<svg
		class={`iceberg-shape pointer-events-none fixed z-10 mt-[-1px] ${scrollY.current && scrollY.current > 50 ? 'opacity-80' : 'opacity-100'}`}
		viewBox="0 0 1233 123"
		xmlns="http://www.w3.org/2000/svg"
		preserveAspectRatio="none"
	>
		<path
			d="M0,122 L34,23 L108,56 L160,20 L236,60 L282,6 L350,57 L410,23 L478,67 L552,25 L610,71 L666,32 L738,64 L806,22 L868,72 L936,28 L1012,62 L1072,18 L1150,67 L1208,24 L1232,39 L1233,0 L0,0 Z"
			fill="#fafafa"
			style={`filter: drop-shadow(0 4px 6px rgba(0, 0, 0, ${
				scrollY.current && scrollY.current > 50 ? '0.15' : '0.1'
			}))`}
		/>
	</svg>

	{@render children()}
</main>
<Footer />
