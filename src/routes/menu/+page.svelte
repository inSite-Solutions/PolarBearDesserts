<script lang="ts">
	import menu from '$lib/menuData.json';
</script>

<div class="flex flex-col gap-5 px-10 pt-5">
	{#each menu as category}
		<section>
			<h1 class="mx-auto w-fit text-2xl">{category.category}</h1>
			<div class="grid w-full auto-rows-auto grid-cols-2 py-2 text-sm">
				{#each category.items as item}
					<div>{item.name}</div>
					<div class="text-right">${item.price}</div>
				{/each}
			</div>
		</section>
	{/each}
</div>
