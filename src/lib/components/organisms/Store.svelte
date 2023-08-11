<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    import close from '$lib/images/close.png';
    import ball from '$lib/images/ballicon.png';
    import emptyBall from '$lib/images/emptyBall.png';
    import buy from '$lib/images/buy.png';
    import tap from "$lib/sounds/tap.mp4";
    export let open = false;
    let audio: HTMLAudioElement;
    let selected: Number = 0
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
    function selectThis(value: Number) {
        selected = value
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
                    <h1>COMPRE MAIS RASPADINHAS AGORA!</h1>
                </div>
                <button class={selected === 0 ? 'select-option active' : 'select-option'} on:click={()=>selectThis(0)}>
                    <div class="select-option-content">
                        <div class="qtd-container">
                            <div class="ball-icon">
                                <img height="100%" width="auto" src={selected === 0 ? ball : emptyBall} alt="ball icon" />
                            </div>
                            <h1 class="qtd">01</h1>
                        </div>
                        <h1 class="value">R$ 1,00</h1>
                    </div>
                </button>
                <button class={selected === 1 ? 'select-option active' : 'select-option'} on:click={()=>selectThis(1)}>
                    <div class="select-option-content">
                        <div class="qtd-container">
                            <div class="ball-icon">
                                <img height="100%" width="auto" src={selected === 1 ? ball : emptyBall} alt="ball icon" />
                            </div>
                            <h1 class="qtd">02</h1>
                        </div>
                        <h1 class="value">R$ 2,00</h1>
                    </div>
                </button>
                <button class={selected === 2 ? 'select-option active' : 'select-option'} on:click={()=>selectThis(2)}>
                    <div class="select-option-content">
                        <div class="qtd-container">
                            <div class="ball-icon">
                                <img height="100%" width="auto" src={selected === 2 ? ball : emptyBall} alt="ball icon" />
                            </div>
                            <h1 class="qtd">05</h1>
                        </div>
                        <h1 class="value">R$ 5,00</h1>
                    </div>
                </button>
                <button class="buy-button" on:click={closing}>
                    <img height="100%" width="auto" src={buy} alt="ball icon" />
                    <h1>CONFIRMAR</h1>
                </button>
            </div>
        </div>
    {/if}
    <audio src={tap} bind:this={audio}></audio>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    .buy-button {
        // text-align: center;
        cursor: pointer;
        background: none;
        border: none;
        margin-left: 50%;
        transform: translateX(-50%);
        height: 60px;
        position: relative;
        h1 {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.2rem;
        }
    }
    .select-option {
        cursor: pointer;
        background: transparent;
        border: none;
        height: 60px;
        width: calc(100% - 20px);
        background-image: linear-gradient(to right,  #a46b00, #fff17b);
        margin: 2px 10px;
        border-radius: 100px;
        padding: 5px;
    }
    .active {
        background-image: linear-gradient(to right,  #006a30, #d4ec3b);
    }
    .select-option-content {
        height: 100%;
        display: flex;
        justify-content: space-between;
        background: #ecb000;
        border-radius: 100px;
    }
    .ball-icon {
        border: 1px solid #33333334;
        border-radius: 100px;
        padding: 3px;
        margin: 3px;
        height: 75%;
    }
    .qtd {
        margin-top: 5px;
        font-size: 2rem;
    }
    .value {
        margin-top: 10px;
        margin-right: 10px;
    }
    .qtd-container {
        display: flex;
    }
    .content {
        margin-top: 36px;
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