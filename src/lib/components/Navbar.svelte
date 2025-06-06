<script lang="ts">
    import { fly } from 'svelte/transition';
    let open = $state(false);

    
    const closeMenu = () => {
        open = false;
    }
</script>

<nav class="flex flex-wrap z-40">
	<div class='flex flex-wrap'>
		<img class='w-[20%]' src="/images/logo.png" alt="" />
		<img class='w-[70%]' src="/images/logoText.png" alt="" />
		{#if open}
        <div class="flex flex-row navigation absolute h-full w-full" transition:fly={{x: 100, duration: 500}}>
            <button class='w-[30%]' onclick={() => {{open = !open}}}></button>
            <div class='flex flex-col items-center pt-5 gap-3 bg-gray-500/90 right-0 w-[70%]'>
            <a href='/' class='text-secondary'>Home</a>
            <a href='/menu' class='text-secondary'>Menu</a>
            <a href='/about' class='text-secondary'>About</a>
            </div>
		</div>
        {/if}
        <button onclick={() => {{open = !open}}}>+</button>
	</div>
</nav>
