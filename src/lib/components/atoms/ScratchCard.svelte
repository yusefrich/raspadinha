<script lang="ts">
    // import { sound } from "svelte-sound";
    // import tap from "$lib/sounds/tap.mp4";
    import tap from "$lib/sounds/kickball.mp3";
    import defaultImage from '$lib/images/cover.png';
    import defaultImagePrize from '$lib/images/prize.png';
    export let cover = defaultImage;
    export let prize = defaultImagePrize;
    export let scratched = false;
    let audio: HTMLAudioElement;

    function scratchCard() {
        audio.play();
        scratched = true
        if (audio.paused) {
            audio.play();
        }else{
            audio.currentTime = 0
        }
    }

</script>

<section class="zoom-animation">
    <button on:click={scratchCard}>
        {#if !scratched}
            <img src={cover} alt="scratch" />
        {/if}
        {#if scratched}
            <img src={prize} alt="scratch" />
        {/if}
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
        background: white;
        border-radius: 2px;
        margin: 2px;
        @include md {
            margin: 5px;
            border-radius: 5px;
        }
        :hover{
            transform: scale(1.04);
            transition: transform 0.5s;
            cursor: pointer;
        }
    }
    img {
        width: 19vw;
        height: 19vw;
        padding: 2px 2px 0px 2px;
        border-radius: 5px;
        @include md {
            padding: 5px;
            width: 14vw;
            height: 14vw;
        }
    }
</style>