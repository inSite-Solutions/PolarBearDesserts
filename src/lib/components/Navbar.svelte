<script lang="ts">
    import { fly } from 'svelte/transition';
    let open = $state(false);

    
    const closeMenu = () => {
        open = false;
    }
</script>

<nav class="w-full relative">
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
    <div
      class="flex flex-row navigation absolute h-full w-full top-0 left-0"
      transition:fly={{ x: 100, duration: 500 }}
    >
      <button
        class="w-[30%]"
        onclick={() => (open = !open)}
        aria-label="close navigation menu"
      ></button>
      <div
        class="flex flex-col items-center pt-5 gap-3 bg-gray-500/90 w-[70%]"
      >
        <a href="/" class="text-secondary">Home</a>
        <a href="/menu" class="text-secondary">Menu</a>
        <a href="/about" class="text-secondary">About</a>
      </div>
    </div>
  {/if}

</nav>

