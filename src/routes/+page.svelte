<script lang="ts">
	import files from '$lib/imageData.json';
	import emblaCarouselSvelte from 'embla-carousel-svelte';
	import Autoplay from 'embla-carousel-autoplay';

	let options = { loop: true };
	let plugins = [Autoplay()];
</script>

<div
	class="pointer-events-none absolute inset-0 z-0 bg-[url('/images/grain.png')] bg-repeat opacity-25"
></div>

<div class="flex flex-col gap-5 px-10 pt-5">
	<section class="flex flex-col gap-5">
		<h1 class="mx-auto w-fit text-2xl">Featured Items</h1>
		<div class="h-52 overflow-hidden rounded-lg" use:emblaCarouselSvelte={{ options, plugins }}>
			<div class="flex">
				{#each files.images as image}
					<div class="h-full w-full flex-none">
						<img
							class="h-full w-full object-cover object-center"
							src={image.src}
							alt={image.alt}
							title={image.title}
						/>
					</div>
				{/each}
			</div>
		</div>
	</section>
	<hr class="text-secondary mx-10" />
	<section>
		<h1 class="mx-auto w-fit text-2xl">Hours</h1>
		<div class="grid w-full auto-rows-auto grid-cols-2 px-10 py-2 text-sm">
			<div class="flex flex-col gap-2">
				<span>Mon - Thu</span>
				<span>Fri - Sun</span>
			</div>
			<div class="flex flex-col items-end gap-2">
				<span>12pm - 10pm</span>
				<span>12pm - 11pm</span>
			</div>
		</div>
	</section>
	<hr class="text-secondary mx-10" />
	<section>
		<h1 class="mx-auto w-fit text-2xl">Location</h1>
		<div class="flex flex-col items-center justify-center gap-2 py-2 pb-5 text-sm">
			<p class="p-0 text-center">6060 Blundell Richmond, BC V7C 5J9</p>
			<div class="z-20 overflow-hidden rounded-lg">
				<iframe
					title="google location"
					src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d5218.793927087424!2d-123.1580072!3d49.155073!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x54860b316a5231e3%3A0xef31fdb7c92c9071!2zUG9sYXIgQmVhciBTd2VldCBIb3VzZSDljJfmnoHnhornlJzlk4HlsYs!5e0!3m2!1sen!2sca!4v1749168176789!5m2!1sen!2sca"
					class="w-full max-w-max border-0"
					loading="lazy"
					referrerpolicy="no-referrer-when-downgrade"
				></iframe>
			</div>
		</div>
	</section>
</div>
