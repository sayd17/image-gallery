<script>
    import images from './Images'
    export let index;
    export let toggleLightbox;
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    $: dispatch('toggled', toggleLightbox);

    const prev = () => {
        if (index > 0) index = index - 1; 
    }

    const next = () => {
        if (index < images.length - 1) index = index + 1; 
    }

</script>

<div class="lightbox" >

    <span class="overlay-left">
        <img class="btn-look" on:mousedown={() => prev()} src="/assets/arrow-left.png" alt="left arrow" width="40px" height="50px" />
    </span>
    
    <img on:mousedown={() => toggleLightbox = !toggleLightbox} src={images[index].src} alt="lightbox" width="30%" height="400px" />
    
    <span class="overlay-right arrow-width ">
        <img class="btn-look" on:mousedown={() => next()} src="/assets/arrow-right.png" alt="left arrow" width="40px" height="50px" />
    </span>
</div>

<style>

    .lightbox {
        position: relative;
        margin-top: 5%;
        margin-bottom: 5%;
        width: 100%;
        text-align: center;
        height: 400px;
        background-color: white;
        overflow: auto;
    }

    .btn-look {
        background-color: lightcoral;
    }

    .overlay-left {
        width: 20px;
        height: 20px;
        position: absolute;
        top: 50%;
        transform: translate(0, -50%);
        z-index: 10;
        text-align: center;
    }

    .overlay-right {
        width: 20px;
        height: 20px;
        position: absolute;
        top: 50%;
        left: 65%;
        transform: translate(-200%, -50%);
        z-index: 10;
        text-align: center;
    }

</style>