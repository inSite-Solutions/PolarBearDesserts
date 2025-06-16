<script lang="ts">
	import '../app.css';
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { scrollY } from 'svelte/reactivity/window';
	let { children } = $props();
</script>

<Navbar />
<main class="bg-primary relative z-40">
	{@render children()}
</main>
<Footer />
