<script>

    import images from './Images'
    export let index;
    export let toggleLightbox;
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    $: dispatch('toggled', toggleLightbox);
    
</script>

<div class="lightbox" on:mousedown={() => toggleLightbox = !toggleLightbox}>
    <img src={images[index].src} alt="lightbox" width="400px" height="400px" />
</div>

<style>

    .lightbox {
        margin-top: 5%;
        margin-bottom: 5%;
        position: absolute;
        width: 100%;
        align-items: center;
        text-align: center;
        height: 100%;
        background-color: white;
        overflow: auto;
    }

</style>