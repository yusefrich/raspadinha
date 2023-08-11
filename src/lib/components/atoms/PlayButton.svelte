<script lang="ts">
    // import { sound } from "svelte-sound";
    import { createEventDispatcher } from 'svelte';
    // import tap from "$lib/sounds/tap.mp4";
    import tap from "$lib/sounds/kickball.mp3";
    import defaultImage from '$lib/images/play.png';
    import defaultImageHightlight from '$lib/images/highlight.png';
    export const cover = defaultImage;
    export const hightlight = defaultImageHightlight;
    let audio: HTMLAudioElement;
    
    const dispatch = createEventDispatcher();
    
    function scratchCard() {
        dispatch('scratch');
        audio.play();
        if (audio.paused) {
            audio.play();
        }else{
            audio.currentTime = 0
        }
    }
    
</script>

<section>
    <button class="play-button" on:click={scratchCard}>
        <img class="play" src={cover} alt="play button" />
    </button>
    <div class="">
        <img class="hightlight rotate" src={defaultImageHightlight} alt="play button" />
    </div>
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
        bottom: 4vh;
        @include md {
            right: 2vw;
            bottom: 3vw;
        }
        @include _md {
            left: 9vw;
        }
    }
    .hightlight{
        position: absolute;
        bottom: 0;
        padding-right: 3vw;
        padding-bottom: 6vw;
        width: 80vw;
        height: 80vw;
        @include md {
            padding-right: 1vw;
            padding-bottom: 2vw;
            right: 0;
            width: 22vw;
            height: 22vw;
        }
    }
    .play {
        width: 65vw;
        height: 65vw;
        @include md {
            width: 18vw;
            height: 18vw;
        }
    }
</style>