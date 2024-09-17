<script>
  	import Thumbnail from "./components/Thumbnail.svelte";
	import images from "./components/Images"
	import Lightbox from "./components/Lightbox.svelte"
	
	let toggleLightbox = false;
	let index = 0;

	const setLightbox = (ind) => {
		toggleLightbox = !toggleLightbox;
		index = ind;
	}

</script>

<main>

	{#if toggleLightbox}
		<Lightbox index={index} on:toggled={(event) => toggleLightbox = event.detail} toggleLightbox={toggleLightbox}/>
	{/if}

	{#if !toggleLightbox}
		<Thumbnail>
			{#each images as image, index (index)}
			<span>
				<img class="hover-effect" src={image.src} on:mousedown={() => setLightbox(index)} alt={image.desc} width="160" height="160" />
			</span>
			{/each}
		</Thumbnail>
	{/if}
	
</main>

<style>
	.hover-effect:hover {
		transform: scale(1.1);
		transition: transform 0.3s ease, opacity 0.3s ease;
		opacity: 0.9;
	}
	
</style>