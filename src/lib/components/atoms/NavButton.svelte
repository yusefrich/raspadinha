<script lang="ts">
    // import { sound } from "svelte-sound";
    // import tap from "$lib/sounds/tap.mp4";
    import { createEventDispatcher } from 'svelte';
    import tap from "$lib/sounds/tap.mp4";
    import defaultImage from '$lib/images/inventory.png';
    export let image = defaultImage;
    const dispatch = createEventDispatcher();
    let audio: HTMLAudioElement;
    
    function clicking() {
        dispatch('cclick');
        audio.play();
        if (audio.paused) {
            audio.play();
        }else{
            audio.currentTime = 0
        }
    }
</script>

<section>
    <button class="play-button" on:click={clicking}>
        <img class="play" src={image} alt="nav button" />
    </button>
    <audio src={tap} bind:this={audio}></audio>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    button {
        border: none;
        background: none;
        padding: 0;
    }
    section {
        // background: white;
        position: relative;
        border-radius: 2px;
        margin: 2px;
        @include md {
            margin: 5px;
            border-radius: 5px;
        }
    }
    .play-button:hover{
        transform: scale(1.04);
        transition: transform 0.5s;
        cursor: pointer;
    }
    .play-button{
        z-index: 10;
        position: relative;
    }
    .play {
        width: 15vw;
        height: 15vw;
        @include md {
            width: 7vw;
            height: 7vw;
        }
    }
</style>