<script lang="ts">
    // import { sound } from "svelte-sound";
    // import tap from "$lib/sounds/tap.mp4";
    import defaultImage from '$lib/images/auto.png';
    import tap from "$lib/sounds/kickball.mp3";
    import { createEventDispatcher } from 'svelte';
    export const cover = defaultImage;
    let audio: HTMLAudioElement;
    const dispatch = createEventDispatcher();
    
    function scratchAll() {
        dispatch('scratchAll');
        audio.play();
        if (audio.paused) {
            audio.play();
        }else{
            audio.currentTime = 0
        }
    }

</script>

<section>
    <button class="play-button" on:click={scratchAll}>
        <img class="play" src={cover} alt="play button" />
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
        @include md {
            right: 35px;
            bottom: 40px;
        }
    }
    .play {
        width: 20vw;
        height: 20vw;
        @include md {
            width: 8vw;
            height: 8vw;
        }
        // @include md {
        //     width: 14vw;
        //     height: 14vw;
        // }
    }
</style>