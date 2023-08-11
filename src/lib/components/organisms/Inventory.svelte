<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    import close from '$lib/images/close.png';
    import tap from "$lib/sounds/tap.mp4";
    import defaultBall from '$lib/images/ball.png';
    export let open = false;
    let audio: HTMLAudioElement;
    const dispatch = createEventDispatcher();

    function closing() {
        dispatch('close');
        audio.play();
        if (audio.paused) {
            audio.play();
        }else{
            audio.currentTime = 0
        }
    }

</script>

<section>
    {#if open}
        <div class="modal-container">
            <div class="modal-content">
                <button class="close-btn" on:click={closing}>
                    <img width="100%" height="100%" src={close} alt="close" />
                </button>
                <div class="content">
                    <h1>Suas raspadinhas!</h1>
                </div>
                <div class="display">
                    <img src={defaultBall} alt="">
                    <h1>15</h1>
                </div>
            </div>
        </div>
    {/if}
    <audio src={tap} bind:this={audio}></audio>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    .content {
        margin-top: 36px;
    }
    .display {
        text-align: center;
        margin-top: 50px;
        h1 {
            font-size: 3rem;
        }
    }
    h1 {
        font-size: 1.5rem;
        margin: 0;
        letter-spacing: -0.1rem;
        font-family: 'Montserrat', sans-serif;
        font-weight: 800;
        color: #00441f;
    }
    .close-btn {
        cursor: pointer;
        background: transparent;
        border: none;
        width: auto;
        height: 30px;
        position: absolute;
        right: 10px;
        top: 10px;
    }
    .modal-container {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 4000;
        width: 100vw;
        height: 100vh;
        background: rgba(0, 0, 0, 0.5);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .modal-content{
        background: #ecb000;
        border-radius: 20px;
        position: absolute;
        height: 90vh;
        top: 5vh;
        left: 5vw;
        width: 90vw;
        @include md {
            width: 40vw;
            left: 30vw;
        }
    }
</style>