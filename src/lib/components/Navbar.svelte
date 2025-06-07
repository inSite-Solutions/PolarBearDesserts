<script lang="ts">
    import { fly } from 'svelte/transition';
    import { scrollY } from 'svelte/reactivity/window';

    let open = $state(false);
</script>

<!-- you can ignore the scrollY undefined error -->
<nav class={`sticky bg-secondary top-0 left-0 w-full z-50 transition-all duration-300 
${scrollY.current > 50 ? 'opacity-80 shadow-lg' : 'opacity-100'}
`}>
  <div class="flex items-center justify-between w-full px-3">
    <img class="w-[20vw] h-auto" src="/images/logo.png" alt="Logo" />
    <div class="absolute left-1/2 -translate-x-1/2">
      <img class="w-[50vw] h-auto" src="/images/logoText.png" alt="Logo Text" />
    </div>
    <button onclick={() => (open = !open)} aria-label="open navigation menu">
      <img src="/icons/Menu.png" alt="" class="w-[10vw] h-auto" />
    </button>
  </div>

  {#if open}
    <div class="fixed inset-0 z-40 flex" transition:fly={{ x: 100, duration: 500 }}>
      <button
        class="w-[30%] h-[100vh]"
        onclick={() => (open = !open)}
        aria-label="close navigation menu"
      ></button>
      <div
        class="flex flex-col items-center pt-5 gap-3 bg-gray-500/90 w-[70%] h-[100vh]"
      >
        <a href="/" class="text-secondary text-2xl" onclick={() => (open = false)}>Home</a>
        <a href="/menu" class="text-secondary text-2xl" onclick={() => (open = false)}>Menu</a>
        <a href="/about" class="text-secondary text-2xl" onclick={() => (open = false)}>About</a>
      </div>
    </div>
  {/if}

</nav>

